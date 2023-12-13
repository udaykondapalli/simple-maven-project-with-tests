node ('node') {
tools {
       // install the maven version configured as "M3" and add it to the path maven 'M3'
       maven "M3"
   }
   
   stages {

           stage('Build') {
               steps {
                  checkout scm

                  // run maven on a unix agent
                  sh "mvn -Dmaven.test.failure.ignore=true clean package"

                  //to run maven on a windows agent,use 
                  // bat "mvn -Dmaven.test.failure.ignore=true clean package"
               }
               post {
                  // if maven was able to able to run the tests ,even if some of the test
                  //failed,record the test results and archive the jar file
                  success {
                     junit '**/target/surefire-reports/Test-*.xml'
                     archiveArtifacts 'target/*.jar'
                  }
               }
           }

   }
   
}
