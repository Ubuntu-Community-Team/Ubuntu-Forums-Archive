---
title: "cron running on incorrect days"
date: 2013-01-14
forum: Server Platforms
---

### Post by quser on 2013-01-14
Hi All,

The following entry in my crontab is excecuted daily, when it should only run on the 1st and 16th of the month:

30 4 1,16 * 0,6 touch /home/quser/testfile >/dev/null 2>&1
30 2 1,16 * 1-5 touch /home/quser/testfile >/dev/null 2>&1

Unless I'm missing something completely obvious, testfile should be created at 2:30 am Monday-Friday, and at 4:30 am on Saturday and Sunday, but only when it is the 1st or 16th of the month.  However, testfile is created every day, either at 2:30 am (Monday-Friday) or 4:30 am (Saturday, Sunday).

This is on Ubuntu Server 12.04.1 LTS, with the latest updates applied.

Any idea what's going on?

Thanks!

---

### Post by craigp84 on 2013-01-14
Specifying day-of-month and day-of-week are treated as OR conditions, which is weird because all other fields are AND'd together.

Have no idea why, but there's a stanza explains the situation in the crontab man page.

Hope this helps,

---

### Post by SlugSlug on 2013-01-14
Not sure if this will help:
[http://www.csgnetwork.com/crongen.html](http://www.csgnetwork.com/crongen.html)

---

### Post by quser on 2013-01-14
That was the problem...  I was sure this was a bug, but apparently it's a feature.  From man 5 crontab:

"      Note: The day of a command's execution can be specified by two fields —
       day  of  month,  and day of week.  If both fields are restricted (i.e.,
       aren't *), the command will be run when either field matches  the  cur&#8208;
       rent time.  For example,
       ``30 4 1,15 * 5'' would cause a command to be run at 4:30 am on the 1st
       and 15th of each month, plus every Friday. One  can,  however,  achieve
       the  desired result by adding a test to the command (see the last exam&#8208;
       ple in EXAMPLE CRON FILE below)."

Thanks!

---

