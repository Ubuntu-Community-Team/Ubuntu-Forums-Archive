---
title: "incured a hassle when installing tomcat7, need your help!!!"
date: 2011-11-27
forum: Server Platforms
---

### Post by jaylonDon on 2011-11-27
my computer config :

Linux***** 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

my problem:
when i install tomcat7 by executing cmd : ~$ sudo apt-get install tomcat7,
i got this: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tomcat7
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.5 kB of archives.
After this operation, 418 kB of additional disk space will be used.
Get:1 [http://**.archive.ubuntu.com/ubuntu/](http://**.archive.ubuntu.com/ubuntu/) oneiric/universe tomcat7 all 7.0.21-1 [37.5 kB]
Fetched 37.5 kB in 0s (63.2 kB/s)
Preconfiguring packages ...
Selecting previously deselected package tomcat7.
(Reading database ... 169316 files and directories currently installed.)
Unpacking tomcat7 (from .../tomcat7_7.0.21-1_all.deb) ...
Processing triggers for ureadahead ...
Setting up tomcat7 (7.0.21-1) ...

Creating config file /etc/default/tomcat7 with new version
Adding system user `tomcat7' (UID 115) ...
Adding new user `tomcat7' (UID 115) with group `tomcat7' ...
[COLOR=Red]Not creating home directory `/usr/share/tomcat7'.
 * tomcat7 is not installed
invoke-rc.d: initscript tomcat7, action "start" failed.
```

it appears i fail to install Tomcat7,but i don't know where is problem. can anyone give me some advice? [SIZE=-1]Thanks in advance&#65281;[/SIZE]

---

### Post by hirenmistry on 2012-07-30
I got same error in Ubuntu 12.04

apt-get install tomcat7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  tomcat7-docs tomcat7-admin tomcat7-examples libtcnative-1
The following NEW packages will be installed:
  tomcat7
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
Need to get 0 B/37.3 kB of archives.
After this operation, 356 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package tomcat7.
(Reading database ... 212671 files and directories currently installed.)
Unpacking tomcat7 (from .../tomcat7_7.0.26-1ubuntu1.1_all.deb) ...
Processing triggers for ureadahead ...
Setting up tomcat7 (7.0.26-1ubuntu1.1) ...

Creating config file /etc/default/tomcat7 with new version
Adding system user `tomcat7' (UID 116) ...
Adding new user `tomcat7' (UID 116) with group `tomcat7' ...
Not creating home directory `/usr/share/tomcat7'.
 [COLOR=RED]* [COLOR] tomcat7 is not installed
invoke-rc.d: initscript tomcat7, action "start" failed.

---

### Post by krige on 2013-03-15
I got the same error trying to install Tomcat 7 on Ubuntu 12.10 Server 64 bit.

```

sudo apt-get install tomcat7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libtcnative-1
The following NEW packages will be installed:
  tomcat7
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/37.3 kB of archives.
After this operation, 356 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package tomcat7.
(Reading database ... 66047 files and directories currently installed.)
Unpacking tomcat7 (from .../tomcat7_7.0.26-1ubuntu1.1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up tomcat7 (7.0.26-1ubuntu1.1) ...
 [COLOR="#FF0000"]*[/COLOR] tomcat7 is not installed
invoke-rc.d: initscript tomcat7, action "start" failed.
```

When I try to start it I get:

```

~$ sudo service tomcat7 start
 * tomcat7 is not installed
```

and then when I try to install it I get:

```

~$ sudo apt-get install tomcat7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tomcat7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by krige on 2013-03-15
I fixed it following these instructions [http://askubuntu.com/a/268271/15242](http://askubuntu.com/a/268271/15242)

---

