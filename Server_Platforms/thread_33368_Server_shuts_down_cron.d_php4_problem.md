---
title: "Server shuts down: cron.d php4 problem?"
date: 2005-05-10
forum: Server Platforms
---

### Post by batigolix on 2005-05-10
hi,

My server shuts down unexpectedly every now and than.

I had a look at the system log at /var/log/syslog and see that the last logged action is a CRON action 

> May 10 18:39:02 ardiles /USR/SBIN/CRON[7479]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)

I found it back in /etc/cron.d/php4

> # /etc/cron.d/php4: crontab fragment for php4
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php4/maxlifetime
# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rmphp4 (END)

now I understand more or less what this purpose is, but i haven't got php4 running. so why is it there? 

can it be the cause of my server to stop, or the computer to shutdown ... (the log doesnt show whether it was shutdown correctly or not)

or am i completely wrong¿?¿

i uncommented the line in cron.d to see what happens.

i run ubuntu 5.04

any help, advice or suggestion is highly appreciated

---

### Post by LordHunter317 on 2005-05-10
No, there is no way that could cause your computer to shutdown unless your hardware was faulty.  It's possible however, that that script is provoking faulty hardware which is causing a kernel panic.

---

### Post by batigolix on 2005-05-10
is there a log that gives more information than the last line in the syslog? maybe some info on the faulty hardware... (what can it be? the hard disk?)

it stopped working this morning as well. the last line from the syslog was the same
> May 10 06:39:02 ardiles /USR/SBIN/CRON[27804]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
and why is that cron action theren when i am not running php4?

---

### Post by LordHunter317 on 2005-05-10
[QUOTE=batigolix]is there a log that gives more information than the last line in the syslog?[/quote]If it was a panic, it might have gotten logged in /var/log/kern.log, but probably not.  

> and why is that cron action theren when i am not running php4?You must have a php4 package installed.

---

