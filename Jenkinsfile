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
                  withAWS(region:'us-east-1',credentials:'aws-static') {
                  sh 'echo "Upload content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'stage_index.html', bucket:'jpipeline')
                  }
              }
         }
      }
}
