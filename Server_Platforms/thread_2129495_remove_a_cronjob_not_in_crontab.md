---
title: "remove a cronjob not in crontab?"
date: 2013-03-26
forum: Server Platforms
---

### Post by wlraider70 on 2013-03-26
I'm getting this log about once a minute

```

Mar 26 10:51:01 philo CRON[11394]: (root) CMD (/usr/bin/php /usr/share/obm/www/cron/cron.php)
Mar 26 10:51:01 philo CRON[11393]: (CRON) info (No MTA installed, discarding output)

```

I know that obm is removed, in fact there's no obm folder in /usr/share
my crontab only has 2 entries and they are for dropbox. 


How do I stop the job?

---

### Post by thnewguy on 2013-03-26
When you say the job isn't in your crontab, have you checked the users' crontabs too?

---

### Post by wlraider70 on 2013-03-26
No, I only did sudo crontab -e

I assume you are saying each user has a crontab, and that this job could be on anyone of those??? I thought there was only 1 file.
If so, is there an easy way to access each crontab rather than logging into them?
Where is the crontab located?

---

### Post by schragge on 2013-03-26
To see who has crontabs
```
sudo ls /var/spool/cron/crontabs
```
To change the crontab for user *alice*
```
sudo -u alice -e crontab
```
Besides, check the file */etc/crontab* as it also may contain cronjobs.

---

### Post by wlraider70 on 2013-03-26
thanks for help all.

I also used [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Ultimately I found my issue in /etc/cron.d.
there was a file named obm-core which I of course deleted.

---

