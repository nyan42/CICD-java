pipeline {
    agent any

    stages {
        stage('Clean') {
            steps {

                // Run Maven on a Unix agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean clean"

            }

        stage('Build') {
            steps {

                // Run Maven on a Unix agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean build"

            }

        stage('Package') {
            steps {

                // Run Maven on a Unix agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean package"

            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
