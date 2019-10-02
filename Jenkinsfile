node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"

    tag = "latest"
    appName = "frontend"
    registryHost = "rnlsoshk1/"
    imageName = "${registryHost}${appName}:${tag}"
    env.BUILDIMG=imageName
    env.BUILD_TAG=tag

    stage "Build"

        sh "docker build -t ${imageName} ."

    stage "Push"

        sh "docker push ${imageName}"

    stage "Deploy"

        kubernetesDeploy configs: "kubernetes/master/*.yaml", kubeconfigId: 'ecsdemo_kubeconfig'
}