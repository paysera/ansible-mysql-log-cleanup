# ansible-mysql-log-cleanup

Clean up mysql/mariadb log files in a docker container

## Requirements

This role requires Ansible 2.8 or higher and platform requirements are listed in the metadata file.

## Role variables

|Name|Default value|Description|
|--|--|--|
|`mysql_log_cleanup_image`|`"mariadb:10.3.22"`|Image that it is used for creating clean up container|
|`mysql_log_cleanup_network`|**NONE**|(REQUIRED) Networks list to attach to|
|`mysql_log_cleanup_volume`|**NONE**|(REQUIRED) Volume name where log file is persisted|
|`mysql_log_cleanup_filename`|`"mariadb-slow.log"`|Log file name|
|`mysql_log_cleanup_log_type`|`"slow"`|Log that should cleaned type. Currently only `slow` logs cleanup is supported|
|`mysql_log_cleanup_database_host`|`"localhost"`|Database host|
|`mysql_log_cleanup_database_user`|`"root"`|Database username|
|`mysql_log_cleanup_database_password`|`"pass"`|Database password|
|`mysql_log_cleanup_database_port`|`3306`|Database port|

## Example playbook

```
- name: Provision servers
  hosts: all
  become: true
  roles:
    - ansible-mysql-log-cleanup
  vars:
    mysql_log_cleanup_image: "mariadb:10.3.22"
    mysql_log_cleanup_network:
        - name: "foo_network"
    mysql_log_cleanup_volume: foo_volume
    mysql_log_cleanup_filename: "mariadb-slow.log"
    mysql_log_cleanup_log_type: "slow"
    mysql_log_cleanup_database_host: localhost
    mysql_log_cleanup_database_user: root
    mysql_log_cleanup_database_password: pass
    mysql_log_cleanup_database_port: 3306
```
