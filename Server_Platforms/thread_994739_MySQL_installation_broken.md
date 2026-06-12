---
title: "MySQL installation broken"
date: 2008-11-27
forum: Server Platforms
---

### Post by Dimas on 2008-11-27
Hi,

I was playing with MySQL but i tried to uninstall. It doesn't uninstall correctly (some errors occurred with "aptitude remove --purge mysql-server-5.0"). So I tried to remove manually:

```

root@somines:/var/lib# rm -R /usr/bin/mysql
root@somines:/var/lib# rm -R /usr/share/mysql
root@somines:/var/lib# rm -R /var/lib/mysql
root@somines:/var/lib# rm -R /var/log/mysql
root@somines:/var/lib# rm -R /etc/mysql/
root@somines:/var/lib# rm -R /etc/init.d/mysql
root@somines:/var/lib# dpkg --purge mysql-server-5.0

```

And then it seems to be uninstalled. But I can't install it now.

```

Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                            [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                            [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

root@somines:/var/lib# /etc/init.d/mysql start
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                            [fail]

```

Some idea? :(

---

### Post by Dimas on 2008-11-27
I tried 'apt-get remove --purge mysql-common' and reinstall again, but:

```

Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                            [ OK ]
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                            [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because the error message indicates its a followup error from a previous failure.
               ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

