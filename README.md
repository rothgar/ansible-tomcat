Tomcat Server
========

Installs java and tomcat to the desired hosts.

Requirements
------------

RHEL/CentOS
Should work with Debian/Ubuntu but is untested

Playbook Example
----------------

```
- hosts: all
  roles:
      - role: rothgar.tomcat_and_java
            openjdk: True
```

Role Variables
--------------
main.yml

```
# Install variables
# Make sure your versions are compatible http://tomcat.apache.org/whichversion.html
tomcat_version: '7.0.50' # 6.0.39 latest 6.x release
java_version: '7u51'
java_build: 'b13'
jdk_or_jre: jre
openjdk: False # Set to true to use openjdk instead of oracle java
http_port: 8080
https_port: 8443

# Environment variables
java_home: /opt/{{ jdk_or_jre }}1.{{ java_version|replace('u','.0_') }} # Use when installing jdk
jre_home: /opt/{{ jdk_or_jre }}1.{{ java_version|replace('u','.0_') }}/jre # Use when installing jre only
catalina_base: /opt/apache-tomcat-{{ tomcat_version }}
catalina_home: /opt/apache-tomcat-{{ tomcat_version }}
catalina_tempdir: /opt/apache-tomcat-{{ tomcat_version }}/temp

# User management
tomcat_user: tomcat
tomcat_user_home: /opt/{{ catalina_home }}/tmp
tomcat_uid: '500'
manager_user: manager-gui
manager_password: managersecret
```

Dependencies
------------

None

License
-------

BSD

Author Information
------------------

Justin Garrison
@rothgar
justingarrison.com
