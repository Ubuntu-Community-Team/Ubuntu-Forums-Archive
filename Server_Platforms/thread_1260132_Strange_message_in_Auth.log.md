---
title: "Strange message in Auth.log"
date: 2009-09-07
forum: Server Platforms
---

### Post by bilbo0a on 2009-09-07
i checked my auth.log file and find these messages.
why are they there? and why are there so many of them?

thanks for help.


Sep  7 20:30:01 WebServerHome CRON[3111]: pam_unix(cron:session): session opened                                      for user root by (uid=0)
Sep  7 20:30:02 WebServerHome CRON[3111]: pam_unix(cron:session): session closed                                      for user root

---

### Post by wojox on 2009-09-07
I believe it's cron updating the message of the day every ten minutes.

---

### Post by DaithiF on 2009-09-07
Hi,
nothing strange about these, just evidence of your cron daemon waking up every minute , to check for any scheduled jobs it needs to run.

If your not familiar with cron, then take a look at these:
```
man cron
man crontab
```

If you want to turn off these messages, you can do that by following the instructions here:

[http://ubuntuforums.org/showthread.php?t=1256801](http://ubuntuforums.org/showthread.php?t=1256801)

---

### Post by bilbo0a on 2009-09-08
thanks for the reply, now i understand and problem solved

---

