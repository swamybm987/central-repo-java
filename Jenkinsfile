pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post{
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deployto tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'b8a338b4-1b76-40e4-9be4-c416f16ea8ac', path: '', url: 'http://43.204.217.61:8080/')], contextPath: null, war: '**/*.war'
            }            
        }
    }
}
