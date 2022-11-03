pipeline {
    agent any

    stages {
        stage('AWS STS') {
            steps {
                echo 'AWS STS'
                sh 'aws sts get-caller-identity'
            }
        }
        stage('AWS LISTAR S3') {
            steps {
                sh 'aws s3 ls'
            }
        }
        stage('GIT CLONE') {
            steps {
                sh 'rm -rf jenkins-git/'
                sh 'git clone https://github.com/oskofo2022/jenkins-git.git'
                sh 'ls -lrt jenkins-git/'

            }
        }
        stage('Upload to S3') {
            steps {
                sh 'aws s3 cp jenkins-git s3://jenkinsbucketfinal --recursive'

            }
        }
    }
}
