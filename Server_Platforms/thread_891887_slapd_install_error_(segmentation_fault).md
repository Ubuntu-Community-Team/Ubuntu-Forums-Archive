---
title: "slapd install error (segmentation fault)"
date: 2008-08-16
forum: Server Platforms
---

### Post by thi3d on 2008-08-16
Hi!
I've been running Ubuntu as a home server for a while, and configuring by editing conf-files and using webmin. I recently changed computer decided to use ebox instead of webmin. Somehow something went wrong (I probably answered some questions to hasty...), and i located the problems to the ldap-server (which I don't actually know what it is). More precisely, the problem occurs when installing "slapd". I've been searching around, but can't find a solution so now I'm turning to you. When using apt-get (or aptitude) I get this:

```
sudo apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ldap-utils
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1355kB of archives.
After this operation, 3625kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 116309 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.9-0ubuntu0.8.04.2_i386.deb) ...
Setting up slapd (2.4.9-0ubuntu0.8.04.2) ...
  Moving old database directory to /var/backups:
  - directory unknown... done.
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... Segmentation fault
Failed to slapadd this data: 
dn: dc=
objectClass: top
objectClass: dcObject
objectClass: organization
o: .
dc: 

dn: cn=admin,dc=
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {crypt}OnMGraB7YhG.s
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone out there have a solution (other then reinstalling ubuntu)??

Regards, 
Marcus

---

### Post by SpoooK on 2009-08-24
bump

---

