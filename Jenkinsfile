pipeline {
    agent { label 'maven-label' }

    tools {
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/sog1-app/core-app.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean deploy"
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}

