---
title: "Samba File Share Server with User Monitoring"
date: 2010-10-23
forum: Server Platforms
---

### Post by yameen101 on 2010-10-23
We have Ubuntu Server edition with Samba file share for our docs and spread sheet files. We have 10 workstations (mixed of XP and Ubuntu desktop. We have 20 users who works in different hours at workstations.

We want to monitor the activity of every user including the files created, modified and deleted by each user. Number of prints taken by each user with file name and number of pages printed on our print server.

Is it possible to get log of each user activities at ubuntu server?

Kind Regards 
Muhammad Yameen

---

### Post by kenada on 2010-11-17
I am also interested in this. Anyone?

---

### Post by capscrew on 2010-11-17
Although I have never used it, there is ```
smbstatus
```
See ```
man smbstatus
```

See Morisito's take on it [**_here_**]("http://moiristo.wordpress.com/2008/12/14/monitoring-samba-using-smbstatus/").

---

