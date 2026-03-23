pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh '/usr/bin/docker build -t selva-nginx .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                /usr/bin/docker stop selva-container || true
                /usr/bin/docker rm selva-container || true
                /usr/bin/docker run -d -p 8090:80 --name selva-container selva-nginx
                '''
            }
        }

    }
}