pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/visssssssss/static-website.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sh '''
                echo "Deploying website..."

                # Copy website files to Apache folder
                sudo cp -r * /var/www/html/

                # Set permissions
                sudo chmod -R 755 /var/www/html
                sudo chown -R www-data:www-data /var/www/html

                echo "Deployment Completed!"
                '''
            }
        }
    }

    post {
        success {
            echo "Website Deployed Successfully!"
        }
        failure {
            echo "Deployment Failed!"
        }
    }
}
