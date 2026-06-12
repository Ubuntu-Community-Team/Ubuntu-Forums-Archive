---
title: "[SOLVED] Oracle Express SQL*Plus problem"
date: 2008-11-30
forum: Server Platforms
---

### Post by MouthIFoam on 2008-11-30
I'm attempting to install Oracle database server on Ubuntu server, and I cannot continue with the installation, as I can't log into SQL*Plus. I'm attempting to do so with the command:

```
sqlplus system@XE
```

I receive the following error in listener.log:

```
30-NOV-2008 15:57:13 * (CONNECT_DATA=(SERVICE_NAME=XE)(CID=(PROGRAM=sqlplus)

(HOST=esubuntu)(USER=gustave))) * (ADDRESS=(PROTOCOL=tcp)(HOST=192.168.3.11)(PORT=44276)) 

* establish * XE * 12514
TNS-12514: TNS:listener does not currently know of service requested in connect descriptor
```

I'm attempting to fire up sqlplus locally. My environment variables appear to be correct, from what I can tell as a fledgling Oracle user. Here's a few pertinent ones:

```
ORACLE_SID=XE
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
```

I've followed the [Oracle documentation]("http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHHJEHF") for installation. Section 4.4, the command line portion, is where I'm stuck with the sqlplus issue.

I'm beginning to wonder if the installation from the .deb file wasn't completely a success. Here are a few other bits of troubleshooting info that may be helpful:

Output from the lsnrctl services command:
```
LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 30-NOV-2008 15:11:21

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
    Handler(s):
      "DEDICATED" established:0 refused:0
         LOCAL SERVER
The command completed successfully
```

tnsnames.ora file:
```
# tnsnames.ora Network Configuration File:

XE =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = esubuntu)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = XE)
    )
  )

EXTPROC_CONNECTION_DATA =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
    )
    (CONNECT_DATA =
      (SID = PLSExtProc)
      (PRESENTATION = RO)
    )
  )
```


listener.ora file:
```
# listener.ora Network Configuration File:

SID_LIST_LISTENER =
  (SID_LIST =
    (SID_DESC =
      (SID_NAME = PLSExtProc)
      (ORACLE_HOME = /usr/lib/oracle/xe/app/oracle/product/10.2.0/server)
      (PROGRAM = extproc)
    )
  )

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = TCP)(HOST = esubuntu)(PORT = 1521))
    )
  )

DEFAULT_SERVICE_LISTENER = (XE)
```


This is a fresh install of Oracle 10g Express Edition (version 10.2) on Ubuntu Server 8.04.

Thanks in advance!

---

### Post by MouthIFoam on 2008-12-10
Looks like I've found the problem. As I'd expected, the initial installation hadn't completed successfully. All the Oracle system files were there, but it seems the initial "XE" database was screwed. After removing the package with

**gustave@ubuntu:~$ dpkg --purge oracle-xe**

and reinstalling with the command

[B]root@ubuntu:~# dpkg -i oracle-xe_10.2.0.1-1.0_i386.deb
[/B]
I witnessed the following snippet of output:

[B]Selecting previously deselected package oracle-xe.
(Reading database ... 15328 files and directories currently installed.)
Unpacking oracle-xe (from oracle-xe_10.2.0.1-1.0_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 119: bc: not found
/var/lib/dpkg/tmp.ci/preinst: 119: bc: not found
/var/lib/dpkg/tmp.ci/preinst: 119: bc: not found
test: 119: 0: unexpected operator[/B]


It was easy to see, since it hung at this point. I killed it. I don't believe I'd seen this when I first tried to install Oracle, but hey, I won't rule that out.

The problem is with the "bc" program, which wasn't installed.*apt-get install bc* fixed that all up.

Oracle installed just fine then, and I was able to fire up SQL*Plus without any issues.

[g]

---

