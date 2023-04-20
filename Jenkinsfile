pipeline {
    agent any
    tools {
        maven 'mvn'
    }
    stages {
        stage('GIT_SCM') {
            steps {
                git branch: 'master', credentialsId: 'bd82295c-d2bf-4695-b3c1-75af9c5b5aef', url: 'https://github.com/varunikkurti/Multi_Org.git'
            }
        }
        stage ('BUILD_WITH_MAVEN') {
            steps {
                sh 'mvn install'
            }
        }
        stage ('DEPLOY_TO_TOMCAT') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'fcfad0dd-ebf1-4edd-8225-305320a30c2d', path: '', url: 'http://52.15.125.5:8080')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
