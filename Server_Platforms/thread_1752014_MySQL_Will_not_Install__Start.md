---
title: "MySQL Will not Install / Start"
date: 2011-05-07
forum: Server Platforms
---

### Post by xinapse on 2011-05-07
I have installed / uninstalled mysql about 5/6 times now after reading lots of tutorials with slightly different methods telling me to do so.

THe last thing i did was 

```
apt-get --purge remove mysql-server mysql-common mysql-admin mysql-client

apt-get install mysql-server
```It will not install and i keep getting this error messages

```
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.51a-24+lenny5) ...
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
```Does anyone know how i can fix it?>

---

