@Library('Kubernetes@master') _
podTemplate(
  agentContainer: 'maven',
  agentInjection: true,
  containers: [
    containerTemplate(name: 'maven', image: 'maven:3.9.9-eclipse-temurin-17', command: '', args: ''),
    containerTemplate(name: 'buildah', image: 'quay.io/buildah/stable:v1.35', command: 'sleep', args: '99d', privileged: true, ttyEnabled: true
    , runAsUser: '0'),
    // containerTemplate(name: 'trivy',image: 'aquasec/trivy:latest', command: 'sleep',args: '99d', ttyEnabled: true ),
    
  ]) 
  {

    node(POD_LABEL) {
    stage('Hello World') {
        script {
            helloWorld()  
        }
    }

    stage('Build') {
        container('maven') {
            script {
                echo "i'm inside contaienr maven"
                mavenBuild.build() 
            }
        }
    }
//-------------
  }
}
