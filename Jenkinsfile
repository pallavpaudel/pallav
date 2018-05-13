
node {
    	stage('Source Checkout')
		{
    		checkout([$class: 'GitSCM', branches: [[name: '*/master']],doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '93b385e8-55c5-44be-b003-71af9a78e315', url: 'https://github.com/s3s-tech/devops.git']]])
		}

	stage('Build Package') 
		{   
    		sh 'mvn -f  MAVEN/pom.xml clean package'
		}

    	stage('Archive Artifacts') 
		{
    		archiveArtifacts 'MAVEN/target/*.jar'
		}
   	stage('Approval') 
		{   
    		input 'Approval to deploy to Dev'	
		}
    	stage('Deploy to Dev') 
		{ 
        	echo "Deploying jar to tomcat"
		}

	}