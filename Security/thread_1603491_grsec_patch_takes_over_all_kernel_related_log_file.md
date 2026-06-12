---
title: "grsec patch takes over all kernel related log files"
date: 2010-10-22
forum: Security
---

### Post by box2 on 2010-10-22
I recently installed a vanilla kernel with grsecurity patch.  I enabled logging because I thought "Hey!  How awesome to see all the commands everyone runs no matter what they do to .bash_history!"

End result: /var/log/{messages,kern.log,dmesg,syslog} all get flooded with seemingly the same information at the same time.  What used to be very small log files (under 100kb for sure each) or now multiple mb each per day.  This is very frustrating because it drowns out all my *useful* logs like say for debugging software that doesn't load properly.

I see on other systems people have a /var/log/grsec.log but I talked to the admins and all of them have said that grsec still logs into everything else and makes everything much less useful.  I tried adding a rule in /etc/rsyslog.conf for grsec.* but it does not catch any of the logs and it certainly doesn't stop the other log files from being inundated.

I have scoured the grsec forum but no one seems to talk about it and when they do they are not using rsyslog daemon.  So I am hoping anyone here would have some input on the matter.

---

### Post by OpSecShellshock on 2010-10-23
Not sure how to stop it from writing to the logs in the first place, but I'd think that for active debugging you could use a terminal with something like:

```
tail -f <your-log-here> | grep -v <common identifier for the grsec stuff>
```

As for the rest of it, well, I'd suppose that a security-oriented kernel build would have in mind that it's better to have as much stuff logged as possible. The file size issue can be managed (at least until you find a solution) by moving the historical logs to external storage. Hopefully someone will be able to come up with something a bit more permanent.

---

### Post by box2 on 2011-09-08
Faced with debugging some services and the problem described above was seriously getting in the way... googling for an answer again brought me basically only to this thread.  The rage... oh dear god the rage...

So finally, apparently a year of using linux has taught me a few things, as I finally learned not only to `man rsyslog.conf` but how to actually understand what it's saying.  This is the solution I came up with:

In /etc/rsyslog.conf at the very top of your rules (after the module and global directives), put these lines:

```

# grsec logs
:msg, contains, "grsec" /var/log/grsec.log
:msg, contains, "grsec" ~

```

The first rule will grab all lines headed for syslog with "grsec" anywhere in them, and write them to /var/log/grsec.log.  The next line tells rsyslog not to pass any lines with "grsec" to any other log facility rules.

Congratulations, I win an internet.  Yay!

---

