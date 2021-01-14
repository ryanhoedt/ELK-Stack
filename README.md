## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Stack Diagram](https://github.com/ryanhoedt/ELK-Stack/blob/main/Diagrams/Red%20Team%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook files may be used to install only certain pieces of it, such as Filebeat.

[first_playbook.yml](https://github.com/ryanhoedt/ELK-Stack/blob/main/Ansible/first_playbook.yml) installs and configures the DVWA virtual machines.

[install_elk.yml](https://github.com/ryanhoedt/ELK-Stack/blob/main/Ansible/install_elk.yml) installs and configures the ELK server container. 

[filebeat-playbook.yml](https://github.com/ryanhoedt/ELK-Stack/blob/main/Ansible/filebeat-playbook.yml) installs and configures Filebeat on the DVWA virtual machines.

[metricbeat-playbook.yml](https://github.com/ryanhoedt/ELK-Stack/blob/main/Ansible/metricbeat-playbook.yml) installs and configures Metricbeat on the DVWA virtual machines.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be capable of handling a high level of traffic, distributing traffic between 3 web servers.  This ensures consistent availability, since no one server is overwhelmed. 
The jump box provides a single, restricted point of entry to the network, accessible only from the public IP address of the admin's computer via SSH.  Access to the virtual machines on the network is possible from the ansible container on the jump box.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the services and system logs.
- 'Filebeat'collects and parses system logs from the server and forwards them to Elasticsearch and Logstash for indexing and Kibana for easy visualization.
- 'Metricbeat'records metrics and statistical data and services running on the server such as CPU usage, memory, file system, disk and network input/output statistics and allows them to be viewed in Kibana.

The configuration details of each machine may be found below:

| Name     | Function        | IP Address | Operating System     |
|----------|-----------------|------------|----------------------|
| Jump Box | Gateway         | 10.0.0.10  | Linux (ubuntu 18.04) |
| Web-1    | DVWA Web Server | 10.0.0.11  | Linux (ubuntu 18.04) |
| Web-2    | DVWA Web Server | 10.0.0.12  | Linux (ubuntu 18.04) |
| Web-3    | DVWA Web Server | 10.0.0.13  | Linux (ubuntu 18.04) |
| ELK-VM   | ELK Stack       | 10.1.0.4   | Linux (ubuntu 18.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
97.122.185.50 (My personal computer's public IP address) 

Machines within the network can only be accessed by the Jump Box.
- The Jump Box has access to the Elk server through the ansible container via SSH 10.0.0.10

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible                                                      | Allowed IP Address                                        |
|----------|--------------------------------------------------------------------------|-----------------------------------------------------------|
| Jump Box | via SSH only                                                             | 97.122.185.50 (My personal computer's public IP address)  |
| Web-1    | No, but can access DVWA portal via HTTP at the Load Balancer's public IP | 97.122.185.50; 10.0.0.10 (Jump Box)                       |
| Web-2    | No, but can access DVWA portal via HTTP at the Load Balancer's public IP | 97.122.185.50; 10.0.0.10                                  |
| Web-3    | No, but can access DVWA portal via HTTP at the Load Balancer's public IP | 97.122.185.50; 10.0.0.10                                  |
| ELK-VM   | No, but can access Kibana portal via port 5601                           | 97.122.185.50; 10.0.0.10                                  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps command](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- 'Filebeat'collects and parses system logs from the server and forwards them to Elasticsearch and Logstash for indexing and Kibana for easy visualization.
- 'Metricbeat'records metrics and statistical data and services running on the server such as CPU usage, memory, file system, disk and network input/output statistics and allows them to be viewed in Kibana.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
