---
title: "I need help for installing mysql"
date: 2011-09-06
forum: Server Platforms
---

### Post by tuncaf on 2011-09-06
Hi,

I am new to ubuntu and linux. i just want to use eclipse and mysql on my ubuntu. whenever i try to install mysql i face with that errors on terminal


useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g mysql -s /bin/false -u 114 mysql' returned error code 1. Exiting.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.54-1ubuntu4_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package libmysqlclient-dev.
Unpacking libmysqlclient-dev (from .../libmysqlclient-dev_5.1.54-1ubuntu4_amd64.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.54-1ubuntu4_amd64.deb
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fredp-ppa-natty.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'playdeb.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)


in the end if i click on software center i face with a dialog box, which says one of your package is broken.. but i tried everything to uninstall that broken package(of course broken package is mysql, it says) and i couldn't get rid of that. as a result i cannot use mysql even i cannot uninstall mysql. Thanks your help

---

### Post by zackwasa on 2011-09-08
Hi,

Are you installing those as root or with sudo privileges?

---

### Post by Habitual on 2011-09-08
```
sudo dpkg-reconfigure mysql-server-5.1
```

from [https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)

---

### Post by zackwasa on 2011-09-09
try running:
```

useradd someuser

```
does it work? maybe it will get unlocked after adding a user

run the reconfigure command after that

Please let me know the results

---

