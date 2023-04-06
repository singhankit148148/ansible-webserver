   pipeline
{
    agent { label "agentfarm" }
    stages {
        stage( 'Delete the workspace') {
            steps {
                cleanWs()
            }
        }
        stage( 'Installing Ansible') {
            steps {
                sh 'sudo apt-get update -y && sudo apt-get upgrade -y'
                sh 'sudo apt install -y wget tree unzip ansible python3-pip python3-apt'
            }
        }
        stage( 'Download Ansible Code') {
            steps {
 git credentialsId: 'git-repo-creds', url: 'git@github.com:singhankit148148/ansible-webserver.git'
            }
        }
        stage( 'Run ansible-lint against playbook') {
           steps {
    sh 'docker run --rm -v $WORKSPACE/playbooks:/data cytopia/ansible-lint:4 apache-install.yml'
sh 'docker run --rm -v $WORKSPACE/playbooks:/data cytopia/ansible-lint:4 website-update.yml'
sh 'docker run --rm -v $WORKSPACE/playbooks:/data cytopia/ansible-lint:4 website-test.yml'
}
}
     }
}
