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
          withAWS(region:'us-west-2', credentials:'udacity c3 aws creds') {
              s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'udacitydevops3cicd')
          }
      }
    }
  }
}