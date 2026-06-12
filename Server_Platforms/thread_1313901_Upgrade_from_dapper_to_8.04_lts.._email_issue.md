---
title: "Upgrade from dapper to 8.04 lts.. email issue"
date: 2009-11-04
forum: Server Platforms
---

### Post by adza on 2009-11-04
Hi There, can someone please help me? I've just recently upgraded from 6.06 to 8.04 on my sun ultra60 server platform.. it seems my email doesn't work now.. :S i'm using postfix and have attached my main and master.cf files.. i have been searching forums etc for several days now and cannot see what the issue might be... (tearing hair out.. etc)..

---

### Post by adza on 2009-11-13
*bump* anyone?

---

### Post by kewlrichie on 2009-11-14
What did u choose when upgrading to new version of postfix? Did it ask you about the configs to keep
your old ones, replace with news or see side by side etc...

I would get the fresh default configs for postfix and courier probably in /usr/share/postifx and /usr/share/courier those should be the new ones but if not I would backup the current configs and purge postfix and courier and go through the configs line by line and edit the new default configs using the old one as a guide.

Also if you don't feel like reconfiguring and wanna try and fix it as it is you should post your /var/log/mail.log to see what errors your getting

---

