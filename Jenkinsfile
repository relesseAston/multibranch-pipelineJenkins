pipeline {

    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                bat """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://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@github.com/relesseAston/hello.git']]
                ])
            }
        }

        stage(' Unit Testing') {
            steps {
                bat """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                bat """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                bat """
                echo "Building Artifact"
                """

                bat """
                echo "Deploying Code"
                """
            }
        }

    }   
}
