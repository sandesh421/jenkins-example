
pipeline {
    agent any
    stages {
        stage('SCM Checkout'){
          git 'https://github.com/sandesh421/jenkins-example'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
             steps {
                 sshagent(['d5763664-1a68-492e-a9c3-0f111fe3895f']) {
                 sh 'scp -o StrictHostKeyChecking=no target/*.jar ec2-user@172.31.24.198:/var/lib/tomcat/webapps/'
      }
             }
   }
}
}	
