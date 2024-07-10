pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/rvgarci/inf335-trabalho-05.git'

                // Run Maven on a Unix agent.
                // sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Compile') {
            steps {
                // Compilar o código (substitua pelos comandos específicos do seu projeto)
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                // Executar os testes JUnit
                sh 'mvn test'
                
                // Arquivar resultados dos testes JUnit
                junit 'target/surefire-reports/**/*.xml'
            }
        }
    }
}
