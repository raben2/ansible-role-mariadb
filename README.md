# Ansible Role: MariaDB

Installs MariaDB with support of custom directories and selinux

## Supported platforms

```
CentOS 6 & 7
Ubuntu 14.04
```

## Post install

Run `mysql_secure_installation`

## Requirements

None

## Role Variables

MariaDB version:

```
mariadb_version: 10.1.18
```

Configuration template:

```
mysql_conf_tpl: mysqld.j2
```

Configuration filename:

```
mysql_conf_file: my.cnf
```

### Galera Node installation
provide a set of users to control the cluster

```
mysql_galera_admins:
    - name: galera_admin
      privileges: "*.*:ALL,GRANT"
      host: all
      secret: '*6F7D24BFE9182B69A694610065E88B6DA1790B23'
```
The setup will probably return an error if you sync an existing cluster
it might take a while until the sync is completed.


### Experimental unattended mysql_secure_installation

```
ansible-playbook release.yml --extra-vars "mysql_secure_installation=true mysql_root_password=your_very_secret_password"
```

## Dependencies

None

## Example Playbook

```
- hosts: servers
  roles:
    - { role: raben2.mariadb }
```

## Credits

- [Georg Rabenstein](https://github.com/raben2)
