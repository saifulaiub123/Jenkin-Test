//def ReleaseDir = "c:\inetpub\wwwroot"
pipeline {
			agent any
			stages {
				stage('Source'){
					steps{
						checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/saifulaiub123/Jenkin-Test.git']]])
					}
				}
				stage('Build') {
    					steps {
						bat label: '', script: 'C:\\nuget\\nuget.exe restore JenkinTest.sln'
						
						bat "\"${tool 'MsBuild'}\" JenkinTest.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=C:\\JenkinsDeploy"
						
    					    
    					}
				}
			}
}
