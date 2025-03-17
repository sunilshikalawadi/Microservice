pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B07EA150D83A45CD6E2E7F4B7F3BAB67.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
               }
            }
        }
        
        stage('Verifiy Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B07EA150D83A45CD6E2E7F4B7F3BAB67.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
