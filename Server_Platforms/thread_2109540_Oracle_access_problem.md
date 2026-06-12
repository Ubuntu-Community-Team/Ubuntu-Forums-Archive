---
title: "Oracle access problem"
date: 2013-01-27
forum: Server Platforms
---

### Post by lintothomas on 2013-01-27
Please Help I'm looking for Solution to 'cannot access [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)' errors :

XE version installed is
```
Use "connect username/password@XE" to connect to the database.
SQL> conn system@xe
Enter password: 
Connected.
SQL> select * from v$version;

BANNER
--------------------------------------------------------------------------------
Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production
PL/SQL Release 11.2.0.2.0 - Production
CORE    11.2.0.2.0    Production
TNS for Linux: Version 11.2.0.2.0 - Production
NLSRTL Version 11.2.0.2.0 - Production

```and Ubuntu ver :
```
**System hostname** srvai (127.0.1.1)   
**Operating system** Ubuntu Linux 12.10   
**Webmin version** 1.610   
**Time on system** [Sun Jan 27 16:30:02 2013]("https://srvai:10000/time/")
**Kernel and CPU** Linux 3.5.0-22-generic on x86_64   
**Processor information** Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz, 8 cores   
**System uptime** 1 hours, 27 minutes   
**Running processes** [238]("https://srvai:10000/proc/")   
**CPU load averages** 0.22 (1 min) 0.21 (5 mins) 0.22 (15 mins)   
**CPU usage** 1% user, 1% kernel, 0% IO, 98% idle   
**Real memory** 3.82 GB total, 861.57 MB used
**Virtual memory** 10.31 GB total, 0 bytes used
**Local disk space** 248.88 GB total, 19.71 GB used
```LSNRCTL status :
```
lt@srvai:~$ lsnrctl stat

LSNRCTL for Linux: Version 11.2.0.2.0 - Production on 27-JAN-2013 16:25:25

Copyright (c) 1991, 2011, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.3.102)(PORT=1521)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 11.2.0.2.0 - Production
Start Date                27-JAN-2013 15:28:21
Uptime                    0 days 0 hr. 57 min. 4 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /u01/app/oracle/product/11.2.0/xe/network/admin/listener.ora
Listener Log File         /u01/app/oracle/product/11.2.0/xe/log/diag/tnslsnr/srvai/listener/alert/log.xml
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=192.168.3.102)(PORT=1521)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Services Summary...
Service "XE" has 1 instance(s).
  Instance "XE", status UNKNOWN, has 1 handler(s) for this service...
The command completed successfully

```

---

### Post by cariboo on 2013-01-27
Moved to a thread of it's own, as the thread it was in was several years old, and things have changed quite a bit since then.

---

