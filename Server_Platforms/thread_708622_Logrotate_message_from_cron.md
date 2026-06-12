---
title: "Logrotate message from cron"
date: 2008-02-26
forum: Server Platforms
---

### Post by SumnerBoy on 2008-02-26
Hi, I have just enabled logrotate on my 7.10 headless server. I am new to Linux and Ubuntu but am trying to learn!

I gather this process will tidy up log files, email them to me if they are about to be deleted, etc etc.

However each morning I have a new email from the Cron Daemon with the following message..

sh: 5: invoke-rc.d: not found

I have tried to manually run each of the logrotate entries that are condfigured as daily and they all seem to execute with no problem. 

How do I go about figuring out what is going wrong here?

Thanks in advance,
Ben

---

### Post by BaseRunner on 2008-02-27
Hi Ben,

I am not a cron expert but I searched around a bit.
It seems that the PATH variable that is inherited by the cron daemon is set in /etc/init.d/rc. On my system it is defined like this:
PATH=/sbin:/bin:/usr/sbin:/usr/bin
invoke-rc.d is in /usr/sbin; so check if /usr/sbin is contained there; if not, just append it.
Another possibility is to enter invoke-rc.d fully qualified to all /etc/logrotate.d files that contain it, so just replace the invoke-rc.d entries by /usr/sbin/invoke-rc.d.
I would prefer the first solution personally.

Good luck
Batta

---

### Post by SumnerBoy on 2008-02-27
Thanks Batta.

I checked my /etc/crontab configuration file and it has the following defined...

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

which seems to be ok. However it is obviously not working so I have gone through as you suggested and updated all the logrotate scripts to include the fully qualified /usr/sbin/invoke-rc.d path.

I will check to see if things are resolved tomorrow morning after cron has run and I usually received my error email!

Thanks again for your help.
Ben

---

