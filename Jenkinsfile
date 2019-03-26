pipeline{
	agent {
		docker{
			image 'node:6-alpine'
			args '-p 3000:3000'
		}
	}
	environment{
		CI = 'true'
	}
	stages{
		stage('build'){
			steps{
				sh 'npm install'
			}
		}
		stage('test'){
			steps{
				sh './jenkins/scripts/test.sh'
			}
		}
		stage('deliver'){
			steps{
				sh './jenkins/scripts/deliver.sh'
				input message: 'Finished using the website? (Click "Proceed" to continue)'
				sh './jenkins/scripts/kill.sh'
			}
		}
	}
}
