## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
   - Beats in Use
   - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load balancers protect the servers from denial of service attack. It also distributes traffic between the servers.
A JumpBox protects your VMs from public exposure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.
 
Filebeat is installed as an agent on th servers, it monitors the log files or locations that you specify, collects log events and forwards them either to Elastisearch or Logstash for indexing.

Metribeat takes the metrics and statistics that it collects and ships them to the output you specify. It helps monitor your servers by collecting metrics from the system and the services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box | Gateway  | 10.0.0.4   | Linux            |
| WEB-1    |  VM      | 10.0.0.5   | Linux            |
| WEB-2    |  VM      | 10.0.0.6   | Linux            |
| WEB-3    |  VM      | 10.0.0.9   | Linux            |
| WEB-4    |  VM      | 10.0.0.8   | Linux            |
| ELK-VM1  |  ElkStack| 10.1.0.4   | Linux            |          
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
20.102.56.7

Machines within the network can only be accessed by port 22.
Only the JumpBox has access to the ELK VM 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |      YES            |   20.102.56.7
| WEB-VMs  |      NO             |                      |
| ELK-VM1  |      NO             |   10.1.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible can be run from the command line and will ensureour provisioning scripts run identically everywhere.


The playbook implements the following tasks:
- Install docker.io
- Download and launch a docker elk stack
- Install python-pip

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| 10.0.0.5  
| 10.0.0.6         
| 10.0.0.9       
| 10.0.0.8 

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects linux logs. Which allows us to track logon events, service start and stops. Also failed access attempts.
Filebeat is used to send your log files to Kibana. Filebeeat monitors and collects log events on specified servers.
Metricbeat collects system metrics from the web servers. It looks for drive space usage, drive space avilable for each host and memory usage.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to the ELK VM.
- Update the host file to include web servers 10.0.0.5, 10.0.0.6, 10.0.0.9, 10.0.0.8
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.


- Which file is the playbook? 
- Where do you copy it?_
- Which file do you update to make Ansible run the playbook on a specific machine? 
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?

- ansible-playbook filebeat-playbook.yml

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
