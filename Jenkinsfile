pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                python3 --version
                pip3 install -r requirements.txt
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''
                pkill -f "python3 app.py" || true
                export BUILD_ID=dontKillMe
                nohup python3 app.py > flask.log 2>&1 </dev/null &
                sleep 5
                '''
            }
        }
    }
}