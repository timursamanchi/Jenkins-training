pipeline {
    agent any

    environment {
        MAX_SIZE = 10
        MIN_SIZE = 1
    }
    parameters {
        string(name: 'FATHER',
        defaultValue: 'Vader',
        description: 'Enter Your father’s name')
        
        choice(name: 'AWS_REGION',
            choices: ['us-east-1', 'us-east-2', 'us-west-1', 'us-west-2'],
            description: 'Select the AWS region for deployment.')

    }
    stages {
        stage('Requirements') {
            steps {
                echo 'echo I am your father.  My name is ${params.FATHER}'
            }
        }
        stage('Build') {
            steps {
                echo "I live in ${params.AWS_REGION}"
            }
        }
        stage('Test') {
            steps {
                echo "MAX Size: ${env.MAX_SIZE}"
                echo "MIN Size: ${env.MIN_SIZE}"
                echo 'Testing..3'
                input message: 'Confirm deployment to production...', ok: 'Deploy'
            }
        }
        stage('Report') {
            steps {
                sh 'echo "Production-Report to confirm deployment.." > report.txt'
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}