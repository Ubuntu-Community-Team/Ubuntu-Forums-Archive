---
title: "When cron.weekly runs do the individual scripts log somewhere?"
date: 2018-09-11
forum: Server Platforms
---

### Post by webmuppet57 on 2018-09-11
When cron.daily / .weekly / .monthly runs the fact it has fired logs to /var/logs/syslog like this:

Sep  9 06:47:01 2536-15913-2558 CRON[24276]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))

Does the actual scripts run get logged anywhere, as in the scripts in /etc/cron.daily directory etc?

---

### Post by TheFu on 2018-09-11
cron jobs send their output to the local MTA for delivery based on the userid running the task.  If the crontab entry doesn't redirect stdout and/or stderr somewhere else, it is part of that email.

From the anacron manpage:
```
       If a job generates any output on its standard output or standard error,
       the  output is mailed to the user running Anacron (usually root), or to
       the address  contained  by  the  MAILTO  environment  variable  in  the
       crontab, if such exists.
```
anacron is used for the cron.hourly, .daily, .weekly, .monthly jobs.  Cron has similar behavior for all other crontab entries to my knowledge.

I don't know what happens if an MTA isn't setup.  All my systems have one, an MTA, with aliases to forward emails to a central email server so they aren't lost or forgotten.

---

### Post by SeijiSensei on 2018-09-11
Any script you run from cron should be configured to log itself.  Even something as simple as
```
00 12 * * * sh /path/to/some/script >> /home/me/myscript.log 2>&1
```
That runs /path/to/some/script at noon and appends the result to myscript.log.  The "2>&1" item redirects any error output to the same location.

Usually I have logging defined within the script itself, but sometimes it's just easier to send all the output from the script to a designated log file.

---

