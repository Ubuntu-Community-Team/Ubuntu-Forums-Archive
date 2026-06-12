---
title: "Squid install problem on 6.10 Server"
date: 2007-03-02
forum: Server Platforms
---

### Post by caffienda on 2007-03-02
I am trying to install squid, actually re-install. I did a apt-get remove squid, because it wasn't working right

this is what happens when I install:
```
 sudo apt-get install squid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  squidclient squid-cgi logcheck-database resolvconf smbclient
The following NEW packages will be installed:
  squid
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/609kB of archives.
After unpacking 1581kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package squid.
(Reading database ... 17666 files and directories currently installed.)
Unpacking squid (from .../squid_2.6.1-3ubuntu1.2_i386.deb) ...
Setting up squid (2.6.1-3ubuntu1.2) ...
Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.010 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
 * Restarting Squid HTTP proxy squid                                                                   * Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.010 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.010 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
                              
```

What do I do to resolve this?

---

### Post by jonathan.lees on 2007-03-03
In the /etc/squid/squid.conf file you need to add a line under the Default Section:

```

visible_hostname your_hostname

```
for example visible_hostname proxy1
and then restart squid with:
```

 /etc/init.d/squid restart

```

---

