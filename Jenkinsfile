pipeline {
	agent any
	
	environment { 
		GMAIL_ID = 'thyoun1961'
		GMAIL_PD = 'Newberry1618'
		com.thyoun.tests.enabled = true
	}
	stages{
		stage("build"){
			steps{
				echo 'build stage'
				echo "running ${env.BUILD_ID} on ${env.JENKINS_URL}"
				sh 'mvn -B -DskipTests clean package'
				archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
				
			}
		}
		stage("test"){
			steps{
				echo 'test stage'
				sh 'mvn test'
			
			}
		}
		stage('deploy'){
			when {
				expression {
					currentBuild.result==null || currentBuild.result=='SUCCESS'
				}
			}
			steps {
				//SWITCH = ${com.thyoun.tests.enabled}
				echo 'Deloyment ready'
				sh 'printenv'
			}
		}
}

}
