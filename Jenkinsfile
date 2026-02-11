pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main',
                url: 'git@github.com:sandunranga97/devops-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-flask-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop flask || true
                docker rm flask || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name flask -p 80:5000 devops-flask-app'
            }
        }
    }
}
