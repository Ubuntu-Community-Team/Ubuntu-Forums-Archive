---
title: "[SOLVED] Strange cron activity"
date: 2008-08-30
forum: Security
---

### Post by CaptSaltyJack on 2008-08-30
I've got some cron stuff logged to /var/log/auth.log*

```

Aug 26 08:09:01 gimp CRON[24788]: pam_unix(cron:session): session opened for use
r root by (uid=0)
Aug 26 08:09:01 gimp CRON[24788]: pam_unix(cron:session): session closed for use
r root
Aug 26 08:17:01 gimp CRON[24800]: pam_unix(cron:session): session opened for use
r root by (uid=0)
Aug 26 08:17:01 gimp CRON[24800]: pam_unix(cron:session): session closed for use
r root
Aug 26 08:39:01 gimp CRON[24818]: pam_unix(cron:session): session opened for use
r root by (uid=0)
Aug 26 08:39:01 gimp CRON[24818]: pam_unix(cron:session): session closed for use
r root
Aug 26 09:09:01 gimp CRON[24845]: pam_unix(cron:session): session opened for use
r root by (uid=0)
Aug 26 09:09:01 gimp CRON[24845]: pam_unix(cron:session): session closed for use
r root
Aug 26 09:15:01 gimp CRON[24857]: pam_unix(cron:session): session opened for use
r root by (uid=0)
Aug 26 09:15:01 gimp CRON[24857]: pam_unix(cron:session): session closed for use
r root
Aug 26 09:17:01 gimp CRON[24860]: pam_unix(cron:session): session opened for use
r root by (uid=0)


```

The stuff running every hour on the 17th minute, I get.  /etc/crontab shows that it executes cron.hourly on the 17th minute.  But the 15th minute and 9th minute, I don't get.  It also fires off every 39th minute as well.  How can I track down what's getting fired off at those times??  Heck, /etc/cron.hourly is empty, so what is going on?

---

### Post by yaztromo on 2008-08-30
I have this in my logs too every 17th minute of the hour. I'd be interested to know what it is. My best guess: cron opening a session every hour to check for scripts in cron.hourly.

---

### Post by CaptSaltyJack on 2008-08-30
> **yaztromo said:**
> I have this in my logs too every 17th minute of the hour. I'd be interested to know what it is. My best guess: cron opening a session every hour to check for scripts in cron.hourly.

That's easy, the 17th minute one is just cron.hourly firing off.  Even if it's empty (I just realized this), cron will still log in /var/log/auth.log even if there was nothing to do, because it still did fire off.

So you're good. :)  But for me, the 9th and 39th minute ones are confusing me...

---

### Post by CaptSaltyJack on 2008-09-02
Ahh, found the source of the 9 and 39 minute cron events.

/etc/cron.d/php5:
```

# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/p
hp5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0
 | xargs -r -0 rm

```

---

### Post by Maarek Stele on 2009-01-06
That's good to hear.  My server has been receiving login attempts from Turkey and other places around the world.

---

### Post by pdtpatrick on 2009-01-06
What type of server are you talking about? FTP?

---

