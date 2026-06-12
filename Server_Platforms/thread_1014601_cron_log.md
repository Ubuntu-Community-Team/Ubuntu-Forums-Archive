---
title: "cron log"
date: 2008-12-18
forum: Server Platforms
---

### Post by liung on 2008-12-18
How can I look my cron log ?

My system os is ubuntu 8.04.1 server i386 , I can't find cron file at /var/log/ directory .

---

### Post by MJN on 2008-12-18
Cron's activity is captured by Syslog in /var/log/syslog. You can easily strip out most of the irrelevent stuff with **grep -i cron /var/log/syslog**
 
Mathew

---

