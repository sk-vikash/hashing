pipeline {
  agent any

  options {
    buildDiscarder(logRotator(numToKeepStr: '30'))
    disableConcurrentBuilds()
    timeout(time: 1, unit: 'HOURS')
    timestamps()
    ansiColor('xterm')
  }

  stages {
    stage('### All Pre Defined Variable') {
      steps {
        echo sh(script: 'env|sort', returnStdout: true)
      }
    }
    stage('### Maven')  {
      steps {
         sh 'mvn -v'
         sh 'mvn clean compile'
      }
    }
    stage('### Build Jar')  {
      steps {
         sh 'mvn package'
         sh 'ls -ltra'
      }
    }
    stage('### Clean') {
        steps {
            cleanWs()
        }
    }
  }
}
