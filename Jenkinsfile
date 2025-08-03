pipeline {
    agent any
    environment {
        // Use PATH+EXTRA to append to PATH properly
        PATH = "/usr/bin:/bin:/opt/homebrew/bin"
    }
    stages {

        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/PraveenKuber/Amazon-Jenkins.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
          stage('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('cleaning'){
            steps{
                sh 'mvn clean'
            }
        }

        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }
        stage('validate'){
            steps{
                sh 'mvn validate'
            }
        }

        
    }

  post{

  success{
     echo 'Build success'
  }
    
  failure{
       echo 'Failure in the build'
   }

  }


}
