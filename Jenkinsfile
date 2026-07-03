pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/yashtalaviya5/DevOps-P4-105.git'
            }
        }

        stage('Verify Files') {
            steps {
                echo 'Checking required project files...'

                bat '''
                dir
                if not exist index.html exit 1
                if not exist about.html exit 1
                if not exist contact.html exit 1
                if not exist style.css exit 1
                if not exist script.js exit 1
                '''

                echo 'All files are present ✔'
            }
        }

        stage('Basic Code Check') {
            steps {
                echo 'Running simple validation...'

                bat '''
                findstr "function" script.js
                findstr "body" index.html
                '''

                echo 'Basic validation completed ✔'
            }
        }

        stage('Build') {
            steps {
                echo 'Building static website project...'
                echo 'No compilation required (HTML/CSS/JS project)'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving project files...'
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'PIPELINE SUCCESS ✔ Project built successfully'
        }

        failure {
            echo 'PIPELINE FAILED ❌ Check errors in console output'
        }
    }
}
