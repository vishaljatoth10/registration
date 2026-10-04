pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Starting Java build...'

                bat '''
                    if not exist out mkdir out
                    javac src\\Hello.java -d out
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running application...'

                bat '''
                    java -cp out Hello
                '''
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'

                bat '''
                    if not exist package mkdir package
                    copy out\\Hello.class package\\
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                bat '''
                    if not exist deployed mkdir deployed
                    copy package\\Hello.class deployed\\
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD PIPELINE COMPLETED SUCCESSFULLY!'
        }

        failure {
            echo 'CI/CD PIPELINE FAILED!'
        }
    }
}