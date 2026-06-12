---
title: "problems with disk IO and find"
date: 2013-12-12
forum: Server Platforms
---

### Post by daryl2 on 2013-12-12
Hi There,

I run some AWS ubuntu 12.04 web servers (running ubuntu server), one in particular is quite a decent spec server which we monitor with new relic. This server is just a base install, with php, apache, mysql and a few php and apache mods, nothing more. Recently the server has been executing "find" and absolutely killing the disk I/O. It appears to be happening at the same time each day, which leads me to believe that it is something that ubuntu schedules. 

Firstly i dont really mind that this process has to run, it also appears to  spawn a bunch of lsof threads which chew a bit of CPU. 

My question is
1) how can i get find to do its indexing at a time that suits me (when our web traffic is low which is during certain hours)
2) New relic sends me disk I/O warnings to my mobile saying that the disk IO has been at over 90% for 5 minutes. I need to get these notifications but not outside of business hours (when our traffic is low because i dont really mind too much).

Any help is appreciated.

Thanks
Daryl

---

### Post by daryl2 on 2013-12-13
Ok well i think this has something to do with the log rotates. I moved the mysql installation to a seperate drive because it was freaking massive. 

Im getting this email at the same time the server starts going crazy.

/etc/cron.daily/logrotate:
/usr/bin/mysqladmin: refresh failed; error: 'Unknown error'
error: error running shared postrotate script for '/var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log /var/log/mysql/error.log '
run-parts: /etc/cron.daily/logrotate exited with return code 1

This says to me there is a problem with the log rotation. Is there any way I can repair this or do i just have to debug the cron.daily script. Does anyone know much about these scripts?

---

