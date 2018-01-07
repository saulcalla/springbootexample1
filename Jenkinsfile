#!groovy​

properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', numToKeepStr: '10']]])

stage('build') {
    node {
        checkout scm
        def v = version()
        currentBuild.displayName = "${env.BRANCH_NAME}-${v}-${env.BUILD_NUMBER}"
        
        echo  "${env.BUILD_NUMBER}"
    }
}


def version() {
    def matcher = readFile('pom.xml') =~ '<version>(.+)</version>'
    return matcher ? matcher[0][1] : null
}