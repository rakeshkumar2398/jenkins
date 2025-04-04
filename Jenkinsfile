pipeline {
    agent any

    stages {
        stage('SCM Clone') {
            steps {
                echo 'GET CODE FROM GIT'
				git branch: 'main', url: 'https://github.com/rakeshkumar2398/jenkins.git'
            }
        stage('MAKING WAR') {
            steps {
                echo 'MAKING WAR FILE WITH MAVEN'
				sh 'maven clean install'
            }
        stage('DEPLOYING') {
            steps {
                echo 'DEPLOYING WAR TO TOMCAT'
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.91.155.206:8081/')], contextPath: 'Jenkins-Tomcat', war: '**/*.war'
            }
        }
    }
