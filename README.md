Ansible Playbook for Docker Installation

This repository contains a simple yet effective Ansible playbook designed to automate the installation of Docker on a Linux machine. The playbook ensures a consistent and repeatable setup, saving time and reducing the potential for human error.
Features

    Idempotent: The playbook is designed to be run multiple times without causing unintended side effects.

    Automated: Installs Docker, Docker Compose, and necessary dependencies automatically.

    User Management: Adds the specified user to the docker group, allowing them to run Docker commands without sudo.

    Platform Support: Tested on Ubuntu/Debian based systems.

Prerequisites

Before running this playbook, ensure you have the following on your control machine:

    Ansible: Version 2.9 or newer.

    SSH Access: The user running the playbook must have SSH access to the target machine with appropriate permissions (e.g., sudo access).

    Git: To clone this repository.

Getting Started

Follow these steps to use the playbook to install Docker on your target machine.
1. Clone the Repository

git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name

2. Configure Inventory

Edit the hosts file to specify your target machine(s). Replace the placeholder IP address with the IP of your machine.

[webservers]
<target-server-ip-or-hostname> ansible_user=<ssh-user>

Replace <target-server-ip-or-hostname> with the actual IP address or hostname of your server and <ssh-user> with the SSH user you will be using to connect to it.
3. Run the Playbook

Execute the playbook from your control machine using the ansible-playbook command.

ansible-playbook -i hosts install_docker.yml --ask-become-pass

    -i hosts: Specifies the inventory file.

    install_docker.yml: The name of the playbook file.

    --ask-become-pass: Prompts for the sudo password on the remote machine if required.

Directory Structure

.
├── hosts
├── install_docker.yml
└── README.md

Usage

After the playbook completes, you can log out and log back into your target machine (or run newgrp docker) to apply the group changes. Then, verify the Docker installation with the following command:

docker --version

License

This project is licensed under the MIT License - see the LICENSE file for details.
Contributing

Contributions are welcome! Please feel free to open a pull request or an issue if you have suggestions or find a bug.
