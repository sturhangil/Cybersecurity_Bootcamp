## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/sturhangil/Cybersecurity_Bootcamp/blob/main/Images/Saim_Turhangil_Project_1.png "Logo Title Text 1")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system processes.

The configuration details of each machine may be found below.

| Name                 | Function   | IP Address | Operating System   |
|----------------------|------------|------------|--------------------|
| Jump-Box-Provisioner | Gateway    | 10.0.1.4   | Linux Ubuntu 18.04 |
| Web-1                | Web Server | 10.0.1.5   | Linux Ubuntu 18.04 |
| Web-2                | Web Server | 10.0.1.6   | Linux Ubuntu 18.04 |
| Elk                  | Elk Server | 10.1.0.4   | Linux Ubuntu 18.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner (10.0.1.4) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Public IP Address (You need to allow only from your personal IP address, you can find it from https://www.whatsmyip.org/)

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Only Jump-Box-Provisioner can access to the Elk Server.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | My Public IP         |
| Web-1                | No                  | 10.0.1.4             |
| Web-2                | No                  | 10.0.1.4             |
| Elk                  | No                  | 10.0.1.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it can be deployed quickly in the cases we need to deploy more than one time. Also, it would decrease the possibility of failure.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install Docker Module
- Increase Virtual Memory
- Use more memory
- download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/sturhangil/Cybersecurity_Bootcamp/blob/main/Images/Project1_D1_P4.png "Logo Title Text 1")

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.1.5
- 10.0.1.6

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat: Filebeat allows us to move the log files from one place to another. By this way, the collected log data can be analyzed by Logstash or Elasticsearch.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the all yaml files to /etc/ansible.
- Update the ansible.cfg file to include the correct remote_user. Line 107 must be updated accordingly.
- In the hosts file, Private IP addresses of WebServers and Elk Server must be updated.
- In the filebeat-config.yml, update the IP addresses on lines 1106 and 1806 with your Elk server's IP address.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.
