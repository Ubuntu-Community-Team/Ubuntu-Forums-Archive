---
title: "mysql install error."
date: 2010-05-15
forum: Server Platforms
---

### Post by ja660k on 2010-05-15
hey all,
installing mysql server on ubuntu server 9.04

and i get this error
```

# sudo apt-get install mysql-server mysql-client

...
...
...
* Stopping MySQL database server mysqld                                                                                                                         [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                                                                                                         [ OK ] 
/etc/init.d/mysql: line 123: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up mysql-client (5.1.37-1ubuntu5.1) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ndstate on 2010-05-18
I dont know if its applicable to your situation or not, but I had similar problems and [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) fixed it for me.

Good luck

---

