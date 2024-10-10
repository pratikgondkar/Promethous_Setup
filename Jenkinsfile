pipeline {
    agent any
    stages {
        stage('Code Check') {
            steps {
                git branch: 'main', url: 'https://github.com/pratikgondkar/Promethous_Setup.git'
            }
        }
        stage('Prometheus') {
            steps {
                sh "ansible-playbook -i aws_ec2.yaml test.yml"
            }
        }
        stage('Node-exporter') {
            steps {
                sh "ansible-playbook -i aws_ec2.yaml node_exporter.yml"
            }
        }
        stage('Alertmanager') {
            steps {
                sh "ansible-playbook -i aws_ec2.yaml alertmanager.yml"
            }
        }
        stage('Grafana') {
            steps {
                sh "ansible-playbook -i aws_ec2.yaml grafana.yml"
            }
        }
    }
}
