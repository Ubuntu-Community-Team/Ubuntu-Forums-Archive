---
title: "Cant install OTRS2"
date: 2009-05-15
forum: Server Platforms
---

### Post by anwoke8204 on 2009-05-15
Hi, I am trying to install OTRS2, I tried once before and the install failed, I tried the install again, and I get the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
otrs2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up otrs2 (2.2.4-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf
Replacing config file /etc/otrs/database.pm with new version
Not replacing deleted config file /etc/otrs/Kernel/Config.pm
Not replacing deleted config file /etc/otrs/Kernel/Config/GenericAgent.pm
Not replacing deleted config file /etc/otrs/maintainance.html
Not replacing deleted config file /etc/otrs/cron
Not replacing deleted config file /etc/otrs/fetchmailrc
chmod: cannot access `/etc/otrs/fetchmailrc': No such file or directory
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)


anyone know how I can resolve this so I can get it installed?

Many thanks

---

### Post by anwoke8204 on 2009-05-18
I think this is more of an issue with apt-get, anyone know how I can resolve this?

---

### Post by Osaris on 2009-06-10
hi try

apt-get purge otrs2

then 

apt-get install otrs2

---

### Post by anwoke8204 on 2009-06-12
Tried the purge looked like it was going to remove it, but then it didnt' install

I get the following when I try to install
```

root@srv1:~# apt-get install otrs2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  libnet-ldap-perl otrs2-doc-en otrs2-doc-de
Recommended packages:
  aspell ispell libapache2-mod-perl2 libgd-graph-perl libgd-text-perl
The following NEW packages will be installed:
  otrs2
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 0B/1802kB of archives.
After this operation, 12.0MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package otrs2.
(Reading database ... 79035 files and directories currently installed.)
Unpacking otrs2 (from .../archives/otrs2_2.2.4-1_all.deb) ...
Warning: The home dir /usr/share/otrs you specified can't be accessed: No such f
ile or directory
Adding system user `otrs' (UID 113) ...
Adding new user `otrs' (UID 113) with group `www-data' ...
Not creating home directory `/usr/share/otrs'.
Setting up otrs2 (2.2.4-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf

Creating config file /etc/dbconfig-common/otrs2.conf with new version

Creating config file /etc/otrs/database.pm with new version
granting access to database otrs2 for otrs@localhost: success.
verifying access for otrs@localhost: success.
creating database otrs2: success.
verifying database otrs2 exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password

Creating config file /etc/otrs/Kernel/Config.pm with new version

Creating config file /etc/otrs/Kernel/Config/GenericAgent.pm with new version

Creating config file /etc/otrs/maintainance.html with new version

Creating config file /etc/otrs/cron with new version

Creating config file /etc/otrs/fetchmailrc with new version

Creating config file /etc/apache2/conf.d/otrs2 with new version
This module does not exist!
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SgtDawg on 2010-04-13
This worked for me
```
sudo apt-get install libapache2-mod-perl2-dev
sudo apt-get purge otrs2
sudo apt-get install otrs2
```

---

### Post by tooCanad on 2010-04-15
We installed OTRS and used it for an upgrade project. Worked great on Ubuntu. However, the repository install was problematic. It never worked that well for us, issues with the www-data user for cron and active directory synch for users, and other issues related to the folder structure on Debian systems.

We ended up uninstalling and followed the manual install procedure for debian systems in the OTRS documentation. That did the ticket. You end up with a folder sturcture closer to the RPM based install and closer to the OTRS documentation.

We are just about to roll out a new instance and use it for all of our support operations.

---

### Post by rslrdx on 2010-04-16
fyi, thats an outdated version of otrs, 2.4 has some cool features.

---

