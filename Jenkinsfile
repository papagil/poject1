pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                // Compile the source code of the Maven project
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                // Run the tests of the Maven project
                sh 'mvn test'
            }
        }
        stage('Quality-check') {
            steps {
                // Perform quality checks on the Maven project (e.g., static code analysis, integration tests)
                sh 'mvn verify'
            }
        }
        stage('Package') {
            steps {
                // Package the compiled code into a distributable format (e.g., JAR, WAR)
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            emailext(
                to: 'mistyoky@gmail.com',
                subject: 'JENKINS FEEDBACK - SUCCESS',
                body: 'Here is the feedback from Jenkins: The pipeline completed successfully.'
            )
        }
        failure {
            echo 'Pipeline failed!'
            emailext(
                to: 'mistyoky@gmail.com',
                subject: 'JENKINS FEEDBACK - FAILURE',
                body: 'Here is the feedback from Jenkins: The pipeline failed.'
            )
        }
        always {
            echo 'Pipeline finished.'
            emailext(
                to: 'mistyoky@gmail.com',
                subject: 'JENKINS FEEDBACK from build - ALWAYS',
                body: 'Here is the feedback from Jenkins: The pipeline has finished its execution.'
            )
        }
    }
}
