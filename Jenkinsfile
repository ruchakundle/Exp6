pipeline {
    agent any
    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot' // IIS web root folder
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning project from GitHub...'
                git branch: 'main', url: 'https://github.com/<your-username>/Exp6.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Build Step: Check files in workspace'
                bat 'dir'
            }
        }
        stage('Test') {
            steps {
                echo 'Running HTML validation using tidy...'
                bat 'tidy -qe index.html' // optional, install tidy
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying index.html to IIS folder"
                bat "xcopy /Y index.html ${DEPLOY_DIR}\\"
            }
        }
    }
    post {
        success {
            echo 'Pipeline finished successfully! Visit: http://localhost/index.html'
        }
        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}
