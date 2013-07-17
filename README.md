ansible-cdh-cluster
===================

The available playbooks can be used to:
- setup a CDH based Hadoop cluster via Cloudera Manager and integrated Cloudera Search

- [planned]
  - setup a CDH based Hadoop cluster without the usage of Cloudera Manager
  - install Cloudera Manager on top of an already running Hadoop cluster

Cloudera: www.cloudera.com
Ansible: www.ansibleworks.com

Prerequisites

- oracle jdk1.6 is highly recommended by Cloudera, ensure you have no other java
  version on your cluster nodes. The playbook will install the corresponding
  oracle jdk
- the playbook will connect as user root to the cluster nodes. If you have a desired
  user, edit the header section of the playbooks accordingly
- all your nodes are installed with a plain Debian Squeeze. Cloudera's packages seem
  to work on Wheezy also, but I have not tested it currently.
- ansible is installed on your client, e.g. your workstation, as described under
  http://www.ansibleworks.com/docs/gettingstarted.html, and this Github repo
  has been checked out

What to adjust for your environment ?

- edit config/hosts and replace the node names hadoop-pg-[1-5] by the DNS names
  of your nodes.
  Replace the names for the roles 'namenode', 'jobtracker', 'clouderamanager' accordingly

- edit vars/base.yml and set the corresponding hostname of the node which acts
  as Cloudera Manager node

Ansible usage hints

- add parameter -v/-vv/-vvv for increasing verbose output of the commands
  ansible is executing
- remove parameter -k if you have passwordless ssh connection from your client
  to the cluster nodes

How to handle the playbooks ?

1. setup a CDH based Hadoop cluster via Cloudera Manager including integrated Cloudera Search
- a detailed step-by-step instruction is available at http://www.ymc.ch/en/how-to-install-cloudera-manager-and-cloudera-search-with-support-from-ansible
