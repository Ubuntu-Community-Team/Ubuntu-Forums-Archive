---
title: "weird, or is it OK?"
date: 2007-02-18
forum: Server Platforms
---

### Post by JimTDI on 2007-02-18
I was tailing my Apache2 error.log when I saw the Apache server "caught SIGTERM" then restarted.  My immediate thought was that I was hacked and someone remote rebooted my Apache.

Howver after looking around - it appears my Apache2 error.log has been renamed to error.log.1, and my access.log has beem renamed to access.log.1

Is there some process that shuts Apache2 down, and rotates the log files?  I sure didn't install anything to do that that I know of.

The new .1 version of the logs belong to user "root", and group "adm".

---

### Post by jtc on 2007-02-18
> **JimTDI said:**
> Is there some process that shuts Apache2 down, and rotates the log files?

Yes, and it's called logrotate.

Default it runs from /etc/cron.daily/logrotate

---

### Post by JimTDI on 2007-02-18
> **jtc said:**
> Yes, and it's called logrotate.

Default it runs from /etc/cron.daily/logrotate

Cool!  I've been running the Ubuntu 6.06 server now for a week, and this is the first time I've seen the logs rotate.  I'll have to check the cron.weekly and see if it's there.  I see a few other logs (vsftpd) rotated as well.

Thanks for the info ! !

---

### Post by jtc on 2007-02-18
No, no, no :)

logrotate, as default is only run from /etc/cron.daily/

That doesn't mean that the logs are rotated every day. How often logs are rotated are defined in /etc/logrotate.conf or by the files included from /etc/logrotate.d/

---

### Post by JimTDI on 2007-02-18
> **jtc said:**
> No, no, no :)

logrotate, as default is only run from /etc/cron.daily/

That doesn't mean that the logs are rotated every day. How often logs are rotated are defined in /etc/logrotate.conf or by the files included from /etc/logrotate.d/


I got it now...  I found /etc/logrotate.d has an entry for apache2, and studied it, and now I understand what's going on.  Even just from tailing my Apace log file, I learned alot today.  Funny how Ubuntu has a way of doing that...  :) 

Thanks for your help - I'll sleep better tonight knowing noone restarted my Apache remotely, and that my logs are safe & sound.

---

