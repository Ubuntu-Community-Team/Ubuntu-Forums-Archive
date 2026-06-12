---
title: "Trying to understand logrotate"
date: 2008-09-15
forum: Server Platforms
---

### Post by ngmachado on 2008-09-15
I installed Syslog-ng to have more flexibility in managing system logs.

Syslog-ng relies on logrotate to rotate log files.

In /etc/logrotate.d exists a syslog-ng file:

```

(...)
/var/log/mail.info {
   rotate 4
   weekly
   missingok
   notifempty
   compress
}

/var/log/syslog {
   rotate 7
   daily
   compress
   postrotate
      /usr/sbin/invoke-rc.d syslog-ng reload >/dev/null
   endscript
}
(...)

```

This means that mail.info will be rotated weekly and syslog daily, fine!

The contents of /etc/crontab are the default:

```

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly)

```

Which means that mail.info should be rotated on 6:47 every sunday, and syslog at 6:25 every day. Right? 

But if I run **ls -l /var/log**, I get:

```

(...)
-rw-r----- 1 root   adm    1243 Sep 15 14:44 mail.info
-rw-r----- 1 root   adm    1984 Sep 13 18:57 mail.info.1.gz
(...)
-rw-r----- 1 root   adm   13096 Sep 15 15:01 syslog
-rw-r----- 1 root   adm    3218 Sep 15 06:30 syslog.1.gz
-rw-r----- 1 root   adm    3128 Sep 14 06:28 syslog.2.gz
-rw-r----- 1 root   adm    3026 Sep 13 06:27 syslog.3.gz
-rw-r----- 1 root   adm    6002 Sep 12 06:25 syslog.4.gz
(...)

```

Mail.info rotated Satuday at 18:57 and syslog is rotating daily but at a "random" time!

What is happening? Is it supposed to expect such a weird behaviour from logrotate?

Thanks.

---

### Post by ngmachado on 2008-09-15
No one has an idea about what's going on?

I'm surprised that nobody had never noticed this strange behaviour from cronjobs or logrotate.

---

### Post by rcbruce on 2008-10-16
> **ngmachado said:**
> 
Mail.info rotated Satuday at 18:57 and syslog is rotating daily but at a "random" time!

What is happening? Is it supposed to expect such a weird behaviour from logrotate?

Thanks.

The date and time are not when logrotate rotated the log but when the log was last written to.

---

### Post by lykwydchykyn on 2008-10-16
Actually the date and time would be when logrotate created the compressed file and wrote it to the drive.  Something to keep in mind though, it's not logrotate that is running at 6:47 and 6:25, but cron.daily and cron.weekly.  When cron executes these directories, it sequentially executes the scripts in them.  Therefore, if you have one or more scripts in cron.daily that are (in ASCII order) before your logrotate script, they are going to execute first and logrotate won't execute until they are finished.  

Check the contents of cron.daily and cron.weekly (/etc/cron.daily and /etc/cron.weekly, respectively) and see if there aren't a few other scripts in there.

---

