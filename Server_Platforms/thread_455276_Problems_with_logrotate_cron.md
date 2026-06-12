---
title: "Problems with logrotate cron"
date: 2007-05-26
forum: Server Platforms
---

### Post by chiefbutz on 2007-05-26
I keep getting emails from my Ubuntu Server about an error when executing one of the crons. I am still sort of new to the whole thing, so could anyone help me figure out how to fix it, here is the email, with slight changes so no one can get to my server:

> 
From: Cron Daemon <root@bfhome>
To: [email]root@bfhome[/email]
Subject: Cron <root@bfhome> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>

/etc/cron.daily/logrotate:
sh: line 1: kill: (4249) - No such process




**[COLOR="Red"]PROBLEM FIXED[/COLOR]**
I don't know how I fixed it, but I did.

---

