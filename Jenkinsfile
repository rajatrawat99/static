pipeline {
    agent any
    stages {

        stage('Lint HTML') {
             steps {
                 sh 'tidy -q -e *.html'
                 }
             }
        
       stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-east-2',credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'elasticbeanstalk-us-east-2-077311932223')
                 }
             }
        }
    }
}