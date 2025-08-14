pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        // stage('Set up Go') {
        //     steps {
        //         sh '''
        //             wget https://go.dev/dl/go1.22.3.linux-amd64.tar.gz
        //             sudo rm -rf /usr/local/go
        //             sudo tar -C /usr/local -xzf go1.22.3.linux-amd64.tar.gz
        //             export PATH=$PATH:/usr/local/go/bin
        //             go version
        //         '''
        //     }
        // }
        stage('Unit Test') {
            steps {
                sh '''
                    export PATH=$PATH:/usr/local/go/bin
                    go test ./... -v
                '''
            }
        }
    }

    post {
        always {
            junit '**/TEST-*.xml'
        }
    }
}