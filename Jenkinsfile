pipeline {
  agent any
  tools{
   maven 'M2_HOME'
  }
  environment {
    registry = "oliviakt23/devops-pipeline"
    registryCredential = 'dockerUserID'
}
   stages {
     stage('build'){
      steps {
       sh 'mvn clean'
       sh 'mvn install'
       sh 'mvn package'
    }
  }
    stage('test'){
     steps{
      echo "test step"
        sh 'mvn test'
    }
  }
   stage('deploy'){
     steps{
      script {
        docker.build registry + ":$BUILD_NUMBER"
    }
  } 
   
  }
}
