---
title: "cron.daily jobs aren't running"
date: 2018-01-15
forum: Server Platforms
---

### Post by jfaberna on 2018-01-15
I have Ubuntu 16.04 Server running my application fine, but I need cron.daily jobs to do maintenance.  I've added them to the files in /etc/cron.daily, but they are not running at the time they are supposed to. I can run them by:
```
sudo run-parts /etc/cron.daily
```
When I look in syslog after the time that cron.daily is scheduled to run I only see:
```
Jan 15 06:25:01 mythbuntu CRON[23845]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
```
I don't see any of the messages that the maintenance scripts would put there is they ran.

Ideas?

Jim A

---

### Post by jfaberna on 2018-01-15
odd behavior this morning.  About 1/2 hour (6:55) after the message in the syslog about cron.daily. I decided to reboot the server to see if that might solve things.  At 7:16 I got an email about some of the database maintenance being completed.  I checked all the logs and my cron.daily maintenance scripts had run at 7:01.  Not sure how and what it chose to run the scripts then and not at 6:25 per the crontab.  All the maintenance scripts don't take 15 seconds to run all together.

Any ideas why?

Jim A

---

### Post by SeijiSensei on 2018-01-15
You can use entries in /etc/crontab to run scripts with root privileges at specific times of day, or create a crontab for root in /var/spool/cron/root.  For instance, to run the script "/usr/local/sbin/dbmaint" at 4:31 am every day, edit /etc/crontab and add the line

```
31 4 * * * root /usr/local/sbin/dbmaint
```

Unlike users' crontabs, entries in /etc/crontab include an additional username parameter.  You can run scripts as other users via this method.

---

