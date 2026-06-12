---
title: "sar logs in  /var/adm/sa"
date: 2007-09-27
forum: Sun Sparc Users
---

### Post by RobSand on 2007-09-27
I recently enabled sar (system activity recorder tool) on a Solaris 10 sparc system.

The performance "logs" being recorded in /var/adm/sa are getting quite large, _quite quickly_!  How do I rotate these logs so I keep 7 days worth of logs and everything else gets automatically deleted?  I suspect this is done in the crontab file.  Here are the contents of my crontab file:

0,5,10,15,20,25,30,35,40,45,50,55 * * * 0-6 /usr/lib/sa/sa1
20,40 8-17 * * 1-5 /usr/lib/sa/sa1
**5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A**

I have heard that the line above containing "**sa2**" is supposed to rotate the logs, but it does not appear to be doing so.  Any suggestions are greatly appreciated and thanks ahead of time!

Sincerely,

Rob Sandifer

---

