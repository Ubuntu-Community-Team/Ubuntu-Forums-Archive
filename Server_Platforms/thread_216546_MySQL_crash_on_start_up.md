---
title: "MySQL crash on start up"
date: 2006-07-15
forum: Server Platforms
---

### Post by cptnapalm on 2006-07-15
This is what gets logged when I try to start mysql with mysqld_safe:

060715 16:44:01  InnoDB: Started; log sequence number 0 43675
060715 16:44:01 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
060715 16:44:01 [Note] Starting crash recovery...
060715 16:44:01 [Note] Crash recovery finished.
060715 16:44:01 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'

I tried looking on Google for a MySQL forum, but (and I promise that this is true) Google told me that what I was searching for looked like an automated query from spyware.  Huh?

Anyhow, I have not been able to find much of anything on the kind of error that I am getting.

Any help would be appreciated.

---

### Post by compbrain on 2006-07-16
> **cptnapalm said:**
> This is what gets logged when I try to start mysql with mysqld_safe:

060715 16:44:01  InnoDB: Started; log sequence number 0 43675
060715 16:44:01 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
060715 16:44:01 [Note] Starting crash recovery...
060715 16:44:01 [Note] Crash recovery finished.
060715 16:44:01 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'

I tried looking on Google for a MySQL forum, but (and I promise that this is true) Google told me that what I was searching for looked like an automated query from spyware.  Huh?

Anyhow, I have not been able to find much of anything on the kind of error that I am getting.

Any help would be appreciated.


Does your MySQL installation contain data? If not I recommend running (as root, or with sudo)
[LIST=1]
[*]apt-get remove mysql-server
[*]dpkg -P mysql-server
[*]apt-get clean
[*]apt-get install mysql-server
[/LIST]

---

### Post by cptnapalm on 2006-07-17
Funny thing is that I had done that and then saw your advice.

Worked like a charm.

I would have liked to have been able to fix it without reinstalling though.  Ah well.

---

