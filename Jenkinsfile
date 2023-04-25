pipeline {
    agent any

    stages {
        stage('Git checkout') {
                   steps{
                        git branch: 'master', credentialsId: 'Github', url: 'https://github.com/skuma342/terraform_aws_fastapi.git'
                    }
                }
        stage("build docker image") {
                    steps {
                       dockerImage = docker.build("monishavasu/my-react-app:latest")
                   }
               }
        stage("push docker image") {
            steps {
                withDockerRegistry([ credentialsId: "dockerhubaccount", url: "dockerhub url" ]) {
                        dockerImage.push()
                        }
            }
        }
    }
}
