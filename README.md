#Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network](AzureNetwork/Diagram/network diagram.png) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  _file-metric-playbook.yaml_ 

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
-load balancers help with traffic compression and prevent emerging threats. An advantage of using a jumpbox helps restrict access to a designated machine.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- File beat provides logs about the file system
- Metric beat provides logs based on machine data, such as uptime.

The configuration details of each machine may be found below.

| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| Jump Box   | Gateway    | 10.0.0.5   | Linux            |
| Web-1      | Webserver  | 10.0.0.13  | Linux            |
| Web-2      | Websever   | 10.0.0.12  | Linux            |
| Elk Server | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 114.77.114.188

Machines within the network can only be accessed by jump box provisioner.
- My personal machine, IP:114.77.114.188

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Address |
|------------|---------------------|--------------------|
| Jump Box   | Yes                 | 114.77.114.188     |
| Web-1      | No                  | 10.1.0.4           |
| Web-2      | No                  | 10.1.0.4           |
| Elk Server | No                  | 10.1.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is free open source tool
- Very simple to use, plentiful templates available to create playbooks
- It's flexibility allows enables future cutsomization 
- Can be setup to automate tasks

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install docker python module
- Increase virutal memory
- Download and launch a docker

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.13
- Web-2: 10.0.0.12

We have installed the following Beats on these machines:
- File beat and Metric beat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, collects log events. 
- Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file file to the ansible controle node.
- Update the hosts file to include elk and webservers, in appropriate configuration files.
- Run the playbook, and navigate to Kibana (http://[Host IP]/app/kibana#/home) to check that the installation worked as expected.
