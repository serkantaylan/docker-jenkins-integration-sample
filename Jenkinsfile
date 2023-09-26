node {
    stage('checkout') {
        checkout scm
        env.WORKSPACE = pwd() 
    }
    stage('Build image') {
        dir('docker-jenkins-integration-sample/src/main/java'){
            dockerImage = docker.build("serkan/jenkins-integration-sample:latest", "-f Dockerfile .")
        }
    }
    stage('Push image') {
        withDockerRegistry([ credentialsId: "dockerhub_id ]){
            dockerImage.push()
            dockerImage.push('latest')
        }
    }
}
