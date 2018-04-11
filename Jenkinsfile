pipeline {
    agent { label 'Ansible-Master' }
    
    stages {
    	/*stage ('Code Analysis'){
	    steps {
                withSonarQubeEnv('SonarQube') {
			sh 'mvn clean sonar:sonar'
		}
	    }
	}*/

	stage ('Compile Stage'){
	    steps {
	        withMaven(maven : 'Maven'){
		    sh 'mvn clean package'
		}
	    }
	}

	stage ('Deploy to Nexus'){
	    steps {
	        withMaven(maven : 'Maven'){
		    sh 'mvn deploy'
		}
	    }
	}
	stage ('Deploy to QA'){
	    steps {
	            sh 'sudo ansible-playbook /etc/ansible/main.yml'
	    }
	}

    }
}
