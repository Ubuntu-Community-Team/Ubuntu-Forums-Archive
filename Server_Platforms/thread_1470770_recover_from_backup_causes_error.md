---
title: "recover from backup causes error"
date: 2010-05-03
forum: Server Platforms
---

### Post by krnlcrash on 2010-05-03
Desperate for some help.  

I am running 8.04 Ubuntu server.  Unfortunately a couple of days ago I thought I should upgrade as desktop upgrades usually go without a hitch and are very easy.  I forgot that my server is live with a few websites and a radius server set up just the way I need (took painfully long time to figure out).

Needless to say the upgrade caused many config file changes and many things stopped working.  I panicked since this is a live server so I went straight to the backups to recover my system.  I booted from a live CD and copied the entire system overtop the new one.

Everything that needed to work works, however now I get this message in my mail about every 10-20mins:


Subject: Cron <root@IMwebserver>   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>

xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted


Googling it, I found that its a problem with findutils.  I tried to reinstall findutils with no luck.


My backup script looks like so:
@daily /usr/bin/rdiff-backup --exclude /dev --exclude /tmp --exclude /var/run/cups/cups.sock --exclude /var/log --exclude /mnt --exclude /media --exclude /proc --exclude /sys --exclude /var/cache/apt / /media/removable/BACKUP/rdiff/
(here you can see all that was excluded.  

How can I fix my system so the above e-mail no longer occurs?

---

### Post by richardjh on 2010-05-04
Are you all up to date?
[See this bug]("https://bugs.launchpad.net/ubuntu/+source/findutils/+bug/234345").

Alternatively may be a problem in ```
 /etc/cron.d/php5
```Mine looks like this:

```
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm

```So can you run the command 

```
[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ]  && find /var/lib/php5/ -type f -cmin  +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm
```**as root** without errors? If so copy the above into /etc/cron.d/php5 and all should be well. 


Post back if you still get problems.

---

