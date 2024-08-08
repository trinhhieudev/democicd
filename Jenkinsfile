pipeline {
    agent any
    
    stages {
        stage('Cloning') {
            steps {
<<<<<<< HEAD
                git branch: 'main', credentialsId: '46e77697-be86-4f93-b431-d0bbe5da99ec', url: 'https://github.com/trinhhieudev/democicd.git'
=======
                git branch: 'develop', credentialsId: '46e77697-be86-4f93-b431-d0bbe5da99ec', url: 'https://github.com/trinhhieudev/democicd.git'
>>>>>>> 189d8f250818f1d8a6796539364c582308ed0767
            }
        }
        stage('Restore package') {
            steps {
                bat "dotnet restore democicd.csproj"
            }
        }
        stage('Clean') {
            steps {
                bat "dotnet clean democicd.csproj"
            }
        }
        stage('Build') {
            steps {
                bat "dotnet build democicd.csproj --configuration Release"
            }
        }
        stage('Publish') {
            steps {
                bat "dotnet publish democicd.csproj"
            }
        }
        stage("Stop Services"){
           steps {
                bat "%windir%\\system32\\inetsrv\\appcmd stop sites democicd.com.vn"
                bat "%windir%\\system32\\inetsrv\\appcmd stop apppool /apppool.name:democicd.com.vn"
                bat "echo waiting until service stopped"
             
            }
        }
        stage("Copy to hosted website folder"){
           steps {
                bat "xcopy .\\bin\\Release\\net8.0\\publish C:\\WWW\\DemoCICD /e /y /i /r"
            }
        }
        stage("Start Services"){
           steps {
                bat "%windir%\\system32\\inetsrv\\appcmd start apppool /apppool.name:democicd.com.vn"
                 bat "%windir%\\system32\\inetsrv\\appcmd start sites democicd.com.vn"
               
            }
        }
        
        
    }

}
