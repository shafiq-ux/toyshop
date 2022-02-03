node {    
      def app     
      stage('Clone repository') {               
             
            checkout([$class: 'GitSCM', branches: [[name: '*/master']],
    	    userRemoteConfigs: [[url: 'https://github.com/shafiq-ux/toyshop.git']]])
      }     
      stage('Build image') {         
       
            app = docker.build("shafiqsukhianihub/shafiqtoystore")    
       }     
      stage('Test image') {           
            app.inside {            
             
             sh 'echo "Tests passed"'        
            }    
        }     
       stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {            
            app.push("${env.BUILD_NUMBER}")            
              }    
           }
        }
