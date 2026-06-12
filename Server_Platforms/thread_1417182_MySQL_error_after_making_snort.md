---
title: "MySQL error after making snort"
date: 2010-02-27
forum: Server Platforms
---

### Post by espressobeanie on 2010-02-27
I was following the step-by-step instructions from this tutorial:

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

When I got to this part in the third post:

mysql -u root -p
I keep getting an error message that says: 

ERROR 2002 (HY0000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I narrowed it down to mysql-server-5.0 and I get this error log:

> The following NEW packages will be installed:
  mysql-server-5.0
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
33 not fully installed or removed.
Need to get 0B/23.8MB of archives.
After this operation, 79.7MB of additional disk space will be used.
(Reading database ... 65036 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
I also used a controlling tty and it still returned an error code (1)


The problem was a flag as shown in this thread: [http://ubuntuforums.org/showthread.php?t=1311863](http://ubuntuforums.org/showthread.php?t=1311863)

---

