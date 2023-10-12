pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('rahul-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t rambo/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push rahulrambo9/rambo-flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
