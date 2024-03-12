pipeline {
    agent any
    stages{
        stage('Git-Checkout'){
            steps {
            echo 'Checking out from git-repo'
            git branch: 'main', credentialsId: '843561f8-cba2-4118-8706-46c8bead06ce', url: 'https://github.com/wicktests/pipeline_script.git'
            }
        }
        stage('Build'){
            steps {
                echo 'Building the checked out project'
                bat 'Build.bat'
            }
        }
        stage('Unit'){
            steps{
                echo 'Unit Testing the project'
                bat 'Unit.bat'
            }
        }
        stage('Quality-Gate'){
            steps{
                echo 'Sonarcube Quality gate testing the project'
                bat 'Quality.bat'
                
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploying the Project'
                bat 'Deploy.bat'
            }
        }
    }
    post {
        always{
            echo 'This will always run'
        }
        success {
            echo 'This will only run when successful'
        }
        failure {
            echo 'This will only run if failed'
        }
        unstable {
            echo 'This will only run if the run was marked as unstable'
        }
        changed {
            echo 'This will only run if the state of the pipeline has changed'
            echo 'For example , if the pipeline was previously failing but it is now successful'
        }
    }
}
