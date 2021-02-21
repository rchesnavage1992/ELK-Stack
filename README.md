# WK13Project1
UCB-Week13-Cybersecurity

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/rchesnavage1992/WK13Project1/blob/main/Images/Wk12_Cloud_Security_Network.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above.
Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat_playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Having a load balancer in place allows incoming traffic to be distributed to different servers so that no one server is over loaded. But do this, it prevents any
one server from being over loaded.  The advantages of a jump box is to have a system on a network to access and manage devices that is in a seperate security zone. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address    | Operating System |
|----------|----------|---------------|------------------|
| Jump Box | Gateway  | 104.209.35.161| Linux            |
| Web1     |          | 10.0.0.7      | Linux            |
| Web-2    |          | 10.0.0.6      | Linux            |
| Web-3    |          | 10.0.0.8      | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump_Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
69.209.29.7

Machines within the network can only be accessed by the jump_box.
- Jump_Box: ip - 104.209.35.161

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 104.209.35.161       |
| Elk-Stack| Yes                 | 52.175.217.229       |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It allows IT people to automate small tasks so that they can focus on bigger task.

The playbook implements the following tasks:
- Able to install several containers as one time there for taking less time.
- Installed filebeat
- Installed metric beat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/rchesnavage1992/WK13Project1/blob/main/Images/Elk_docker_ps.png 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.7
- 10.0.0.8
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeats forwards and centralize logs and files and is designed to ship files
- Metricbeats collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK Playbook file to _Install_Elk.yaml.
- Update the hosts file to include the web server and the elk machine
- Run the playbook, and navigate to the elk container and run sudo docker ps to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook?  __The Ansible Configuration File__ Where do you copy it? __You copy it to the YAML file
- _Which file do you update to make Ansible run the playbook on a specific machine? __First you update the hosts file with the correct IP addresses under certain headers, then in the playbook you specifiy under hosts which headers you are installing on__ 
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.175.217.229:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
Command to run the playbook - ansible-playbook install-elk.yaml
Command to update files - nano install-elk.yaml, nano /etc/ansible/host - to add servers
