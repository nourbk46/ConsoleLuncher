   pipeline {
       agent any
       stages {
           stage('Checkout Codebase') {
               steps {
                   cleanWs()
                   git url: 'https://github.com/nourbk46/ConsoleLuncher.git', branch: 'main'
               }
           }
           stage('Build') {
               steps {
                   sh 'mkdir -p lib target'
                   sh 'curl -L -o lib/junit-platform-console-standalone-1.8.1.jar https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.8.1/junit-platform-console-standalone-1.8.1.jar'
                   sh 'javac -d target -cp lib/junit-platform-console-standalone-1.8.1.jar src/test/java/FirstUnitTest.java'
               }
           }
           stage('Test') {
               steps {
                   sh 'java -jar lib/junit-platform-console-standalone-1.8.1.jar -cp target -c FirstUnitTest'
               }
           }
       }
   }
