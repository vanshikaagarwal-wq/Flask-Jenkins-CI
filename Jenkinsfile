pipeline {
    agent any

    stages {

        stage('Checkout Latest Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-ssh-key',
                    url: 'git@github.com:vanshikaagarwal-wq/Flask-Jenkins-CI.git'
            }
        }

        stage('Create Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    source venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Build Flask Application') {
            steps {
                sh '''
                    source venv/bin/activate
                    python -m py_compile app.py
                    echo "Flask application build successful"
                '''
            }
        }

        stage('Test Flask Application') {
            steps {
                sh '''
                    source venv/bin/activate

                    python -c "
from app import app

with app.test_client() as client:
    response = client.get('/')
    assert response.status_code == 200
    print('Flask application test successful')
"
                '''
            }
        }
    }
}pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-ssh-key',
                    url: 'git@github.com:vanshikaagarwal-wq/Flask-Jenkins-CI.git'
            }
        }

        stage('Create Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    source venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test Flask Application') {
            steps {
                sh '''
                    source venv/bin/activate

                    python -c "
from app import app

with app.test_client() as client:
    response = client.get('/')
    assert response.status_code == 200
    print('Flask application test successful')
"
                '''
            }
        }
    }
}
