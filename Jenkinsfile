pipeline {
    
    environment {
        EMAIL_TO = 'prabhu.k@releaseiq.io,prabhukasisekar@gmail.com'
    }
    
   agent any

        stages {
            
        stage('Checkout') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://kaspr001@bitbucket.org/riqio/riq-admin-ui.git']]])
         }
      }
      
        stage('Compile') {
            steps {
                echo 'Compile DONE'
            }
        }
        
        stage('Testing') {
            steps {
                echo 'Testing DONE'
            }
        }
        
        //stage('Git-tag') {

        //steps {

            //withCredentials([usernamePassword(credentialsId: your_credentials, passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {

               // sh "git tag ${your_tag}"
              //  sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@${repository} ${your_tag}"
           // }
       // }
   // }
    
    }
    
    post {  
         success {  
             echo "${env.JOB_NAME} Build & Deploy successful"
             mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}console", cc: '', charset: 'UTF-8', from: 'devops', mimeType: 'text/html', replyTo: '', subject: "Build Success: Project name -> ${env.JOB_NAME}", to: "$EMAIL_TO";  
         }  
         failure {
             echo "${env.JOB_NAME} Build & Deploy failed"
             mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}console", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Build Failed: Project name -> ${env.JOB_NAME}", to: "$EMAIL_TO";  
         }  
     }
    
}
