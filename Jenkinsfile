node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Maven3';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn sonar:sonar"
      -D sonar.projectVersion=1.0-SNAPSHOT \
      -D sonar.login=admin \
      -D sonar.password=admin12345 \
      -D sonar.projectBaseDir=/var/lib/jenkins/workspace/jenkins-sonar/ \
      -D sonar.projectKey=Maven1 \
      -D sonar.sourceEncoding=UTF-8 \
      -D sonar.language=java \
      -D sonar.sources=Maven1/src/main/java/com/affy \
		  -D sonar.tests=my-app/src/test \
      -D sonar.host.url=http://localhost:9000
    }
  }
}