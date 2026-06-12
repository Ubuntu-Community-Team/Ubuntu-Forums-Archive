---
title: "Installing mysql-server causes error"
date: 2016-05-04
forum: Server Platforms
---

### Post by Enforcer83 on 2016-05-04
I get the following while trying to install mysql-server.  Prior to this I installed and removed/purged/autoremoved mariadb after I had issues setting the root password and being unable to login (I tried multiple times).  What do I need to do to successfully install mysql-server?

```
Preconfiguring packages ...Selecting previously unselected package mysql-common.
(Reading database ... 182971 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.7.12-0ubuntu1_all.deb ...
Unpacking mysql-common (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-client-core-5.7.
Preparing to unpack .../mysql-client-core-5.7_5.7.12-0ubuntu1_amd64.deb ...
Unpacking mysql-client-core-5.7 (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.12-0ubuntu1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-server-core-5.7.
Preparing to unpack .../mysql-server-core-5.7_5.7.12-0ubuntu1_amd64.deb ...
Unpacking mysql-server-core-5.7 (5.7.12-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-common (5.7.12-0ubuntu1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) 
in auto mode
Selecting previously unselected package mysql-server-5.7.
(Reading database ... 183123 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.12-0ubuntu1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.12-0ubuntu1_all.deb ...
Unpacking mysql-server (5.7.12-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-client-core-5.7 (5.7.12-0ubuntu1) ...
Setting up mysql-client-5.7 (5.7.12-0ubuntu1) ...
Setting up mysql-server-core-5.7 (5.7.12-0ubuntu1) ...
Setting up mysql-server-5.7 (5.7.12-0ubuntu1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in aut
o mode
mysql_upgrade: Got error: 1524: Plugin 'unix_socket' is not loaded while connecting to the M
ySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a pre
vious failure.
              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by DuckHook on 2016-05-04
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by Enforcer83 on 2016-05-04
Solved it myself.  Had to run the following two commands to start over from scratch.

```

sudo apt-get remove --purge mysql*
sudo apt-get remove --purge mariadb*

```

---

### Post by DuckHook on 2016-05-04
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

