provision-ec2
=========

Role for provisioning of AWS EC2 instance 

Requirements
------------
Role to create Linux and Windows AWS EC2 instance form the AMI image 

Role Variables
--------------

ec2-vars should be defined with below list of variables
ec2_keypair: ""
ec2_image: ""
ec2_subnet_name: ['']
ec2_security_group_name: ['']
ec2_vpc_name: ""
ec2_region: ""
ec2_instance_type: ""
ec2_tag_Role: ""
ec2_tag_EnvironmentGroup: ""
ec2_tag_EnvironmentUse: ""
ec2_tag_Criticality: ""
ec2_tag_EnvironmentType: ""
ec2_tag_Name: ""
ec2_tag_Application: ""
ec2_tag_EnvironmentID: ""
ec2_tag_Project: ""
ec2_tag_StartCron: ""
ec2_tag_StopCron: ""
ec2_volume_size: 
no_of_instances: 
startindex: 1
iam_name: ""
instance_state: present #states: present, absent, running, restarted, stopped


Dependencies
------------

Ansible role vpc-components-inventory should run before and should include variables in vpc-components.json as pre-tasks

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

   - hosts: localhost
   connection: local
   gather_facts: false
   user: root
   pre_tasks:
          - include_vars: ../ec2_vars/{{ cli_environmentid }}/{{ type }}_eu1a.yml
   roles:
     - { role: provision-ec2, ec2_user_data: "", win_initial_password: "", OS_LINUX: LINUX, OS_WINDOWS: WINDOWS, ec2_instance_os: "{{ OS_LINUX }}", iam_name: "{{ec2_tag_Application}}-{{ec2_tag_EnvironmentGroup}}-{{ec2_tag_Role}}" }


License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
