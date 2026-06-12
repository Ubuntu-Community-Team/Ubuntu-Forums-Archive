---
title: "Removing HTTPD"
date: 2011-02-11
forum: Server Platforms
---

### Post by mishra.sandip on 2011-02-11
Hi Experts !!
 
I am trrying to remove apache2 (HTTPD) by using the following command.
 
sudo apt-get remove apache2 
 
But still it is there in etc drive.
 
Please guide how to remove completely the HTTPD service.
 
regards
SAndip

---

### Post by peter_z11 on 2011-02-11
try:
sudo apt-get purge apache2 

man apt-get
purge is identical to remove except that packages are removed and
purged (any configuration files are deleted too).

---

### Post by mishra.sandip on 2011-02-11
oot@ASU-Network-Security:~# sudo apt-get purge apache2
sudo: unable to resolve host ASU-Network-Security
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apache2-utils libaprutil1-dbd-sqlite3 apache2.2-bin libapr1 libaprutil1-ldap
  apache2.2-common apache2-mpm-worker libaprutil1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 216 not upgraded.
root@ASU-Network-Security:~# 


The command is not removing apache2.

I used a scan tool to  view the HTTPD port.I can still see the port.

Discovered open port 22/tcp on 10.0.2.15
Discovered open port 21/tcp on 10.0.2.15
Discovered open port 80/tcp on 10.0.2.15>>>>>Port
Discovered open port 23/tcp on 10.0.2.15
Discovered open port 53/tcp on 10.0.2.1


Please suggest next..

---

### Post by mishra.sandip on 2011-02-11
sudo apt-get remove --purge apache2 apache2-utils
 
 
This command helpd me to remove completely.

---

