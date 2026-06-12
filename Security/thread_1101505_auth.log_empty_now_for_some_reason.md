---
title: "auth.log empty now for some reason"
date: 2009-03-20
forum: Security
---

### Post by Cyked on 2009-03-20
Yesterday my auth.log had a bunch of entries going back to the 15th.  Today when I looked at it I only have the lines from just having ssh'd in.  Why would it purge like that, something I need to check?

I'm seeing these every 17 and 39 of the hour.

```
Mar 20 08:17:02 tux CRON[29338]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 20 08:17:02 tux CRON[29338]: pam_unix(cron:session): session closed for user root
Mar 20 08:39:01 tux CRON[29719]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 20 08:39:01 tux CRON[29719]: pam_unix(cron:session): session closed for user root

```

---

### Post by Pom2122 on 2009-03-20
It's most likely logrotate cleaning it. In /var/log do you also have either auth.log.0 or auth.log.1.gz? If so, they are backups of the rotated log file. :)

---

### Post by Cyked on 2009-03-20
Oh, ok.  :D  Thanks.  I have one that is .0 and 3 gz files.

What about the cron job that keeps running?  I assume its 100% unrelated, just wondering what it is.  I thought it was something I had discovered before, did something to stop because I deemed it wasn't needed, but have since rebooted and its back and have no clue what it is or how to go about finding out what it is by checking jobs on my machine.

---

### Post by Pom2122 on 2009-03-20
You can look at the following: /etc/crontab, /etc/cron.d/*, /etc/cron.daily/*, /etc/cron.hourly/*, /etc/cron.weekly/*, /etc/cron.monthly/* to see what programs are being run. I wouldn't advise deleting any of these unless you're quite sure of what you are doing - they are there to keep your system up to date and running smoothly. :)

---

