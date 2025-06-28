pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning repo...'
                git branch: 'main', url: 'https://github.com/yaminiarumugam/-flask-docker-app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t flask-image .'
            }
        }
        stage('Run Docker Container') {
            steps {
                echo 'Running container...'
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                docker run -d -p 5000:5000 --name flask-container flask-image
                '''
            }
        }
    }
}
