[![Build Status](https://travis-ci.org/novomatic-tech/ansible-role-logstash-in-docker.svg?branch=master)](https://travis-ci.org/novomatic-tech/ansible-role-logstash-in-docker) [![License](https://img.shields.io/badge/license-Apache%202-green.svg)](https://github.com/novomatic-tech/ansible-role-logstash-in-docker/blob/master/LICENSE) [![Ansible Role Name](https://img.shields.io/ansible/role/43133.svg)](https://galaxy.ansible.com/novomatic-tech/logstash_in_docker) [![Ansible Role counter](https://img.shields.io/ansible/role/d/43133.svg)](https://galaxy.ansible.com/novomatic-tech/logstash_in_docker)
# ansible-role-logstash-in-docker
Role to install and configure Logstash container


Role Variables
--------------

All default variables are predefined in [defaults/main.yml](defaults/main.yml).


Example Playbook
----------------

Example playbook usage:

```
- hosts: ubuntu18
  vars:
    logstash_user: "logstash"
    logstash_group: "logstash"
    logstash_service_name: "logstash"
    logstash_image: "logstash:7.2.1"
    logstash_container_name: "logstash"
    logstash_command: '["-f", "/etc/logstash/logstash.conf", "-w", "1"]'
    
    logstash_compose_files_path: "/etc/compose-files"
    
    logstash_monitoring_enabled: true
    logtash_exporter_image: "sequra/logstash_exporter:v0.1.3"
    logstash_exporter_command: "--web.listen-address=:9198 --logstash.endpoint=http://{{ logstash_service_name }}:9600"
    logstash_pipeline: |
      input {
      }
      output {
      }
    logstash_envs: {}
  roles:
    - geerlingguy.docker
    - ansible-role-logstash-in-docker
```

License
-------

Apache 2.0

Author Information
------------------

This role was created in 2019 for the purposes of Novomatic Technologies Poland.

