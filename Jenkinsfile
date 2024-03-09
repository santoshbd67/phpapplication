pipeline {
    agent any
   
    stages {
        stage('git checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/santoshbd67/phpapplication.git'
            }
        }
        
        stage('build and push docker images') {
            steps {
               script{
                   withDockerRegistry(credentialsId: 'dockerhub') {
                       sh "docker build -t phpapp ."
                       sh "docker tag phpapp santoshbd67/phpapp:v1"
                       sh "docker push santoshbd67/phpapp:v1"
                 }
               }
            }
        }
    }
}
