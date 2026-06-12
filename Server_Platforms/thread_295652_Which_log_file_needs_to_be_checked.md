---
title: "Which log file needs to be checked?"
date: 2006-11-08
forum: Server Platforms
---

### Post by ronzo on 2006-11-08
Hi there,

I have an edgy server installation. Today, the system hung - I wasn't able to log in via SSH and was unable to shut it down by pressing the power button. Unfortunately, there is no keyboard or monitor attached to the system. After resetting the system (by holding the power button pressed for > 4 secs) it seems to work fine again. 

But - what to do now? Which logfile needs to be checked to find out what was going on?

Which other logfiles should I check periodically? Are there tools that can check logfiles and inform me if something is not ok?

Is /var/log/auth.log the only log where I can find login attempts to my system?

Thanks in advance for answering my questions!

---

### Post by Jussi Kukkonen on 2006-11-08
Yes, auth.log contains all login attempts.

You might want to look at the *logcheck* package (be prepared to tweak the config to fit your needs).

---

### Post by MJN on 2006-11-08
Do bear in mind that a complete system freeze is unlikely to be captured in a logfile - after all it's unable to do anything nevermind log the fact!

Of course, there might be some clue preceeding the freeze however this is typically not the case.

Worth looking at /var/log/syslog and see if it recorded anything in the minutes prior to this last freeze...

Mathew

---

### Post by ronzo on 2006-11-08
Nothing found in syslog. 

Does 
```

Nov  8 06:25:01 myserver /USR/SBIN/CRON[7697]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
Nov  8 06:25:43 myserver exiting on signal 15
Nov  8 06:25:44 myserver syslogd 1.4.1#18ubuntu6: restart.

```
really mean that the Computer has restarted or is it only a syslog thing? What's "Signal 15"? I found other people having experienced the same problem ([http://ubuntuforums.org/showthread.php?t=245216&page=2)](http://ubuntuforums.org/showthread.php?t=245216&page=2)).

I am sure not to have initiated a reboot at 6:25 today. What might have caused that? (where could I find some info in the logs?)

---

### Post by MJN on 2006-11-08
It's just referring to syslogd restaring. The *exiting on signal 15* is merely referring to a 'standard' termination of the daemon. It restarts in order to start using fresh logfiles (and to free up the 'old' ones available for archiving as required).

As mentioned on the second log line your daily cron jobs are scheduled to kick in at 6:25am every day (if it's on at that time, if not then anacron will ensure they're executed as appicable next time it is turned on).

Mathew

---

