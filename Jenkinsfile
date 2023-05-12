node('master')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuousBuild')
    {
        sh 'mvn package'
    }
    stage('continuousDeployment')
    {
    deploy adapters: [tomcat9(credentialsId: '3180a94a-546f-4dea-a0c1-e62cdb340c64', path: '', url: 'http://172.31.29.5:8080')], contextPath: 'testapp', war: '**\\*.war'
    }
    stage('continuousTesting')
    {
      git credentialsId: '3180a94a-546f-4dea-a0c1-e62cdb340c64', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'  
    }
 stage('continuousDelivery')
 {
    sh 'java -jar /var/lib/jenkins/workspace/testing/testing.jar'
 }
 
}