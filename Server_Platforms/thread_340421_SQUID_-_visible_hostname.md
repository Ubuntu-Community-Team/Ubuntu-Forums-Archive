---
title: "SQUID - visible_hostname"
date: 2007-01-17
forum: Server Platforms
---

### Post by Josh1 on 2007-01-17
So I installed SQUID, but it won't load. Here is the full log (including installing):

```

josh@JOSH:~$ sudo apt-get install squid
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ruby1.8 blop python-qt3 ruby cmt python-sip4 libtunepimp3 libifp4 libruby1.8
  libnjb5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  squid-common
Suggested packages:
  squidclient squid-cgi logcheck-database resolvconf
The following NEW packages will be installed:
  squid squid-common
0 upgraded, 2 newly installed, 0 to remove and 9 not upgraded.
Need to get 1006kB of archives.
After unpacking 6451kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com edgy/main squid-common 2.6.1-3ubuntu1 [415kB]
Get:2 http://au.archive.ubuntu.com edgy/main squid 2.6.1-3ubuntu1 [591kB]      
Fetched 1006kB in 17s (57.0kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package squid-common.
(Reading database ... 120707 files and directories currently installed.)
Unpacking squid-common (from .../squid-common_2.6.1-3ubuntu1_all.deb) ...
Selecting previously deselected package squid.
Unpacking squid (from .../squid_2.6.1-3ubuntu1_i386.deb) ...
Setting up squid-common (2.6.1-3ubuntu1) ...
Setting up squid (2.6.1-3ubuntu1) ...
Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.004 user + 0.004 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
 * Restarting Squid HTTP proxy squid                                             * Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.012 seconds = 0.004 user + 0.008 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.020 seconds = 0.016 user + 0.004 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
                                                                         [fail]

josh@JOSH:~$ squid
FATAL: Unable to open configuration file: /etc/squid/squid.conf: (13) Permission denied
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.000 user + 0.008 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
josh@JOSH:~$ sudo squid
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.024 seconds = 0.004 user + 0.020 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)

```

Any help? Mycomputer name is JOSH.

---

### Post by PetePete on 2007-01-17
you need to edit the /etc/squid.conf. add the follwoing (open with text editor using sudo)

visible_hostname "JOSH"

then cd /etc/init.d
sudo ./squid start

you prob want to read some tutorial about the squid.conf file otherwise you'll never get squid running properly/how you want it :D

---

