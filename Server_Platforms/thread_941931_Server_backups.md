---
title: "Server backups"
date: 2008-10-08
forum: Server Platforms
---

### Post by Doby on 2008-10-08
We have a few linux box's at work, with vtiger, zimbra, and another email running off them.  I am looking for a good backup program to backup the entire system, then run incremental backups.  One like "Time Machine" for Macs or "TimeVault" for ubuntu 7.10 would be great.  Does anyone out there have a good app, or know how to setup timevault on the server side?  Plus it has to be able to run none gui, We have the none gui based server.  Please help.

---

### Post by ruif13 on 2008-10-08
Hi Doby,

i used one with gui web interface (BACULA)

[http://www.bacula.org/](http://www.bacula.org/)

apt-get install bacula-common bacula-console bacula-director-common bacula-fd bacula-sd libpg3 mtx mt-st

and

apt-get install bacula-director-mysql


regards

---

### Post by samosamo on 2008-10-08
If you're a fan of rdiff-backup instead of straight up rsync, you may want to try slbackup plugin for Webmin.  One day, hopefully, someone will code a real web front end to this wonderful tool.

---

### Post by wirelessmonkey on 2008-10-09
> **ruif13 said:**
> Hi Doby,

i used one with gui web interface (BACULA)

[http://www.bacula.org/](http://www.bacula.org/)

apt-get install bacula-common bacula-console bacula-director-common bacula-fd bacula-sd libpg3 mtx mt-st

and

apt-get install bacula-director-mysql


regards

I have to juggest the Community portion of Groundworkopensource
read the forum to get suggesitonsand solutions from developers.

---

