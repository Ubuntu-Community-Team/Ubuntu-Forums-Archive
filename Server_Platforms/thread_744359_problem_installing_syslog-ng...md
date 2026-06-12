---
title: "problem installing syslog-ng.."
date: 2008-04-03
forum: Server Platforms
---

### Post by Mia_tech on 2008-04-03
I'm trying to install syslog-ng, but install goes well except it fail to initialize the appication```
jorge@ubuntu-box:~$ sudo apt-get install syslog-ng
[sudo] password for jorge:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  syslog-ng
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/181kB of archives.
After unpacking 553kB of additional disk space will be used.
Selecting previously deselected package syslog-ng.
(Reading database ... 127274 files and directories currently installed.)
Unpacking syslog-ng (from .../syslog-ng_2.0.0-1ubuntu1.1_i386.deb) ...
Setting up syslog-ng (2.0.0-1ubuntu1.1) ...
 * Starting system logging syslog-ng                                     [fail] 
invoke-rc.d: initscript syslog-ng, action "start" failed.
``` 
any help appreciated thanks

---

### Post by schneider707 on 2008-04-03
i had this problem once and i typed ```
sudo aptitude install syslog-ng
```...worked for me =D

---

### Post by Mia_tech on 2008-04-03
> **schneider707 said:**
> i had this problem once and i typed ```
sudo aptitude install syslog-ng
```...worked for me =D

tried that too...didn't work, I wonder if I first have to remove whatever log application is preinstalled in ubuntu

thanks

---

### Post by Mia_tech on 2008-04-04
does syslog-ng comes with an interface, or  how do I configure it?


thanks

---

