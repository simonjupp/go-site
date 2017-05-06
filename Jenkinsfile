pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        parallel(
          "Initialize": {
            echo 'Hello, Pipeline.'
            
          },
          "Reset": {
            build 'skyhook-reset'
            
          }
        )
      }
    }
    stage('Ready production software') {
      steps {
        parallel(
          "Ready owltools": {
            build 'owltools-build'
            
          },
          "Ready robot": {
            build 'robot-build'
            
          }
        )
      }
    }
    stage('Produce GAFs') {
      steps {
        build 'gaf-production'
      }
    }
    stage('Produce ontology') {
      steps {
        build 'ontology-production'
      }
    }
    stage('Produce derivatives') {
      steps {
        parallel(
          "Produce index": {
            echo 'TODO: index'
            
          },
          "Produce graphstore": {
            echo 'TODO: graphstore'
            
          }
        )
      }
    }
    stage('Publish') {
      steps {
        echo 'TODO: S3 publisher from sshfs'
      }
    }
    stage('Deploy') {
      steps {
        echo 'TODO: deploy AmiGO'
      }
    }
  }
}