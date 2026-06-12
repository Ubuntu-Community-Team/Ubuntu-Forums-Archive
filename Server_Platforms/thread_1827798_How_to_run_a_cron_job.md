---
title: "How to run a cron job?"
date: 2011-08-18
forum: Server Platforms
---

### Post by noscript on 2011-08-18
Hi!
I am running ubuntu 10.10
I have probably quite a simple question,
How exactly do I create a cron job to execute several
php scripts?

I need to run 4 different scripts 

-a 1 Minute script
-a 5 Minute script
-a 1 Hour script
-a 1 Day script

I have tried hunting around google, But I couldn't find a straight forward tutorial to
just get this setup.

Thanks heaps I really appreciate it!

Kiel

---

### Post by Lars Noodén on 2011-08-18
You can edit your crob jobs with the program crontab:

```

crontab -e 

```

The columns are minute, hour, day of month, month, and day of week.
See the [crontab manual](http://manpages.ubuntu.com/manpages/natty/en/man5/crontab.5.html) for more details.

---

### Post by noscript on 2011-08-18
Ok so I have navigated through it, this is what I have so far

1 * * * * php /var/www/cron_run_minute.php
5 * * * * php /var/www/cron_run_five.php
* 1 * * * php /var/www/cron_run_hour.php
0 0 * * * php /var/www/cron_run_day.php

How does that look?

---

### Post by noscript on 2011-08-18
Now how do I actually get it to run?/save?/start?
Do I need to type a particular thing?

---

### Post by arrrghhh on 2011-08-18
> **noscript said:**
> Now how do I actually get it to run?/save?/start?
Do I need to type a particular thing?

Just save the file, and assuming you entered the command correctly, it should "just work".

I sometimes set things to 1 minute just to test to make sure the job runs.  Not sure what these jobs are doing, but I'm sure there's some way you can check to ensure the jobs are running.

Might want to read the Wikipedia on cron, it's very helpful:

[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

Might help you understand the way cron schedules tasks.

Just like -e, ```
crontab -l
``` will list the crontab jobs.

---

### Post by noscript on 2011-08-18
Please bear with me here,
I run this in terminal, I don't see a save option

---

### Post by arrrghhh on 2011-08-18
> **noscript said:**
> Please bear with me here,
I run this in terminal, I don't see a save option

Oh, you've never used Nano?  Crtl-X will exit, and if you've made any changes it'll ask if you want to save them or not.

---

### Post by a2j on 2011-08-18
> **noscript said:**
> Please bear with me here,
I run this in terminal, I don't see a save option

do vi or vim /etc/crontab - you should be able to edit and save that file.

---

### Post by SeijiSensei on 2011-08-18
> **a2j said:**
> do vi or vim /etc/crontab - you should be able to edit and save that file.

Be aware that /etc/crontab has a different syntax than users' crontabs.  /etc/crontab includes a username after the time codes like this:

```
0 * * * * root sh /usr/local/sbin/hourly_script
```

That runs hourly_script as root every hour on the hour.

---

### Post by jibon_24 on 2011-09-10
Thanks I am looking this. ohhhhhhhh

---

