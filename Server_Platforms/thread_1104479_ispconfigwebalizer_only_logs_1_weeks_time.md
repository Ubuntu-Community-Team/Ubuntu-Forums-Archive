---
title: "ispconfig/webalizer only logs 1 weeks time"
date: 2009-03-23
forum: Server Platforms
---

### Post by specail on 2009-03-23
I have been looking through my apache2, httpd, ispconfig conf files and cannot figure out why my server only keeps 1 weeks worth of logs. They get clear out every Sunday.

I found a logfile /root/ispconfig/httpd/logs/access.log that contains information dating back to when i first set up the server a few months ago, but when i try to have webalizer analyze it, i get Error: Can't open log file /root/ispconfig/httpd/logs/access.log

and another odd thing ispconfig is saying my /.Private directory is 42gb, but when i navigate to it, it is empty.

---

### Post by Johnsie on 2009-03-23
Dunno if this is what your ooking for but BBClone is a really good stats logger:

[http://bbclone.de/](http://bbclone.de/)

---

### Post by BkkBonanza on 2009-03-23
There is probably log rotation set up that is moving or deleting your logs from a cron set for Sundays. Try looking around in /etc/cron/weekly for a script that is doing something to your logs. It may show where they are moved to or if being deleted.

Given you have lots of space being used in your Private directory I would guess that maybe they get moved there. You won't see them if the genius who set you up decided it should be hidden files or directories. You can see hidden files by using the -a option with ls (at console) or by typing ctrl-h if in Nautilus.

---

