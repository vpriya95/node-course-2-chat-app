pipeline {
  agent {
    docker {
      image 'node'
      args '-p 3001:3001'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Deploy') {
      steps {
        sh '''curl -X POST \\
  https://api.heroku.com/apps/jd-chat-demo/builds \\
  -H \'Accept: application/vnd.heroku+json; version=3\' \\
  -H \'Authorization: Bearer 6add32f1-c153-4f8a-846b-843019712a6d\' \\
  -H \'Cache-Control: no-cache\' \\
  -H \'Content-Type: application/json\' \\
  -H \'Postman-Token: 083d3df6-3491-4b89-a0de-6cdaf5134752\' \\
  -d \'{
  "source_blob": {
    "url": "https://codeload.github.com/ksawme/node-course-2-chat-app/legacy.tar.gz/master?token=5ce1ed9d48aa9f406acee17b68f224d98c7c0e31"
  }
}\''''
      }
    }
  }
}