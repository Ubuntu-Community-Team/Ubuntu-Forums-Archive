---
title: "cron - what is it why is it giving me errors?"
date: 2011-05-05
forum: Server Platforms
---

### Post by wlraider70 on 2011-05-05
I'm getting this error

CRON[1452]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May  5 10:17:01 hyrule CRON[1485]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


I don't know what it means, not even close. Also, I'm not sure where cron came form. is it a default package?

---

### Post by tgalati4 on 2011-05-06
cron is a chronological job runner.  You have maintenance jobs that run hourly, daily, weekly, etc.

Obviously, a PHP5 job is running.  You could look at the code and see what it is doing:

cat /usr/lib/php5/maxlifetime     

The && notation means if the previous job ran successfully, run the next job.  It's probably looking to refresh a stale cache or page and it checks this hourly.  It was probably set up for some web service that you are running--like drupal, wordpress, sugarcrm, etc.

cron.hourly is a script to run maintenance tasks hourly.  It's a system file.  Again you can read it to see what it does:

cd /etc/cron.hourly
ls

If you have any shell scripts in this directly, they will get run hourly.  I currently have none in my desktop Jaunty installation.  Your server may have a few scripts in there.

If you want to learn more:

man cron
man crontab

I don't see any errors.  It's just an information notice.  Errors are labeled: ERROR.

---

### Post by wlraider70 on 2011-05-06
thanks for the clarification. 
I thought that messages in syslog where all errors.

---

### Post by tgalati4 on 2011-05-06
90% are info.  Errors are clearly marked.

---

