pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/pranavbadhe/docker.git'
            }
        }
        
        stage('Docker Build') {
            steps {
                sh 'sudo docker build -t apache:v1 .'
            }
        }
        
        stage('Remove existing containers') {
            steps {
                sh 'sudo docker rm -f apache'
            }
        }
        
        stage('Docker Run') {
            steps {
                sh 'sudo docker run -itd --name apache -p 80:80 apache:v1'
            }
        }
        stage('Check the status') {
            steps {
                sh 'sudo docker ps'
            }
        }
    }
}
