---
title: "rsyslog not logging to auth.log"
date: 2011-04-19
forum: Server Platforms
---

### Post by jicooo on 2011-04-19
Hello all,
I'm running Ubuntu server 10.04, and my auth.log is no longer getting updated. And actually my auth.log is empty and everything was being logged to auth.log.1, same with syslog, mail, and other logs.

Is that normal for everything to be logged in *.log.1? logrotate had been rotating weekly up until now.

And secondly, any idea why this might be happening? All other logs are fine, and I have the default configs for rsyslog.
I've tried restarting the rsyslog daemon but still no luck :(

---

### Post by klabog on 2011-04-24
[edit]Ubuntu 10.4[/edit]

I'm having the same effect. Wondering if this has to do anything with denyhosts? After setting it up I noticed that auth.log was empty and logging was written to auth.log.1 (same with syslog mail and other logs).
Because of the different name denyhosts didn't work. Suspicious!

Anyone has an idea?

Thanks, Klaus

---

### Post by amandler on 2011-05-25
Hey folks -- I started seeing the same thing on my Ubuntu 10.04 LTS server.  Everything was logging to the .1 log files, and now syslog is not logging at all.  Any insight?

---

### Post by NickD-NLUG on 2011-09-06
I'm seeing the same, and believe it's to do with a race condition between rsyslog and logrotate.

That said... I don't have a solution yet... anyone?

---

