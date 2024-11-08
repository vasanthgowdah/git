pipeline {
    agent any

    stages {
        stage('Git-Checkout') {
            steps {
                echo "Checking out from Git Repo"
                git 'https://github.com/vasanthgowdah/git.git'
            }
        }
        
        stage('Set Permissions') {
            steps {
                sh 'chmod +x Build.sh Unit.sh Deploy.sh'
            }
        }

        stage('Build') {
            steps {
                echo "Building the checked-out Project!"
                sh './Build.sh'
            }
        }
        
        stage('Unit-Test') {
            steps {
                echo "Running JUnit Tests"
                sh './Unit.sh'
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying to stage Environment for more tests"
                sh './Deploy.sh'
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
