// Powered by Kube 

timestamps {

node ('Kubernetes') { 

	stage ('K8s_BnD - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GitHub', url: 'https://github.com/praveenkumarn/spring-boot-websocket-chat-demo']]]) 
	}
	stage ('K8s_BnD - Build') {
 	
// Unable to convert a build step referring to "hudson.plugins.ws__cleanup.PreBuildCleanup". Please verify and convert manually if required.		// Maven build step
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn -f pom.xml clean package " 
			} else { 
 				bat "mvn -f pom.xml clean package " 
			} 
 		}		// Shell build step
sh """ 
#!/bin/bash
pwd
id
ls -lrt
java -version
hostname

sudo -S docker image ls
sudo -S docker container ls

sudo -S kubectl get deployment

sudo -S kubectl get services

sudo -S kubectl delete services kubernetes-springboot

sudo -S kubectl delete -n default deployment kubernetes-springboot

sudo -S docker build -t spring-boot-websocket-chat-demo .

sudo -S kubectl run kubernetes-springboot --image=praveenkumarnagarajan/spring-boot-websocket-chat-demo:0.0.1-SNAPSHOT --port=8080


sudo -S kubectl expose deployment/kubernetes-springboot --type="NodePort" --port 8080

sudo -S kubectl describe services/kubernetes-springboot


sudo -S docker tag spring-boot-websocket-chat-demo praveenkumarnagarajan/spring-boot-websocket-chat-demo:0.0.1-SNAPSHOT

cat ~/pass.txt | sudo -S docker login --username praveenkumarnagarajan --password-stdin

sudo -S docker push praveenkumarnagarajan/spring-boot-websocket-chat-demo:0.0.1-SNAPSHOT 
 """ 
	}
}
}
