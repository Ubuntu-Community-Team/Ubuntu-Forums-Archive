---
title: "Please - is there an easy way to change mail.log rotation to weekly?"
date: 2008-07-17
forum: Server Platforms
---

### Post by jimwillsher on 2008-07-17
Hi all,

Sorry if this is a lamer question, but I've read all manner of website guides including this

[http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/](http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/)

and 

[http://www.freespamfilter.org/forum/viewtopic.php?t=711&start=15](http://www.freespamfilter.org/forum/viewtopic.php?t=711&start=15)

and

[http://stephan.paukner.cc/logbook/archives/185-What-the-hell-is-rotating-my-mail.log.html](http://stephan.paukner.cc/logbook/archives/185-What-the-hell-is-rotating-my-mail.log.html)

and I'm still confused :-(

My mail.log is getting rotated daily:


2008-07-17 08:40 mail.log
2008-07-17 07:09 mail.log.0
2008-07-16 07:24 mail.log.1.gz
2008-07-15 07:01 mail.log.2.gz
2008-07-14 06:50 mail.log.3.gz
2008-07-13 06:46 mail.log.4.gz
2008-07-12 07:49 mail.log.5.gz
2008-07-11 07:10 mail.log.6.gz


I'd prefer it to get rotated weekly (the files will never be very big).

Looking at the guides I need to change /etc/cron.weekly/sysklogd and the equivalent daily file, but I'm really unsure what to change.

Can someone give me an idiot's guide?

I'm running 8.04 as a mailserver and webserver (so headless, no GUI).

Many thanks,



Jim

---

### Post by cdenley on 2008-07-17
Maybe you have to edit /etc/logrotate.d/sendmail. Just a guess.

---

### Post by jimwillsher on 2008-07-17
Thanks, but I'm not using sendmail.

I think it's a sysklogd change that's required.

Cheers, Jim

---

### Post by soulresin on 2008-07-17
> **jimwillsher said:**
> Thanks, but I'm not using sendmail.

I think it's a sysklogd change that's required.

Cheers, Jim

Hi.

AFAIK, sysklogd does not handle rotation.  That's handled by logrotate.

grep for mail.log in /etc/logrotate.d to find which file is handling that,
and change "daily" to "weekly" in the configuration file.

If you can't find which config file handles that, check the main /etc/logrotate.conf to see if it's defaulting to daily rotation.

---

### Post by jimwillsher on 2008-07-18
Many thanks. Unfortunately I still don't seem any closer.

My /etc/logrotate.d directory has:

apache2
apt
aptitude
dkpg
mysql-server
ppp
queezecenter
vsftpd
wpa_action


and none seems to contain "mail".

Now I'm really stumped :-(



Jim

---

### Post by MJN on 2008-07-18
Mail log rotation *is* handled by syslog (not logrotate) hence you were on the right track originally. Off the top of my head I do not know exactly how you want /etc/cron.[daily|weekly]/sysklogd changing but that's where your solution lies. If you get no joy in the next few days I'll try and give it a once over.
 
Mathew

---

### Post by jimwillsher on 2008-07-18
Ok great, many thanks.

What I've now done is edit /etc/cron.daily and replace

logs=$(syslogd-listfiles)

with

logs=$(syslogd-listfiles -s mail.log)


and will see what happens in the morning :-)


Jim

---

### Post by soulresin on 2008-07-18
> **MJN said:**
> Mail log rotation *is* handled by syslog (not logrotate) hence you were on the right track originally. Off the top of my head I do not know exactly how you want /etc/cron.[daily|weekly]/sysklogd changing but that's where your solution lies. If you get no joy in the next few days I'll try and give it a once over.
 
Mathew

Hmm.  I stand corrected.  Thanks for setting me straight.

My apologies to the OP for being off my rocker.

---

### Post by jimwillsher on 2008-07-28
To follow up on this thread, I made the following change to /etc/cron.daily/sysklogd:

```

#! /bin/sh

# sysklogd      Cron script to rotate system log files daily.
#
#               If you want to rotate other logfiles daily, edit
#               this script.  An easy way is to add files manually,
#               to add -a (for all log files) to syslogd-listfiles and
#               add some grep stuff, or use the -s pattern argument to
#               specify files that must not be listed.
#
#               This is a configration file.  You are invited to edit
#               it and maintain it on your own.  You'll have to do
#               that if you don't like the default policy
#               wrt. rotating logfiles (i.e. with large logfiles
#               weekly and daily rotation may interfere).  If you edit
#               this file and don't let dpkg upgrade it, you have full
#               control over it.  Please read the manpage to
#               syslogd-listfiles.
#
#               Written by Martin Schulze <joey@debian.org>.
#               $Id: cron.daily,v 1.14 2007-05-28 16:33:34 joey Exp $

test -x /usr/sbin/syslogd-listfiles || exit 0
test -x /sbin/syslogd || exit 0
test -f /usr/share/sysklogd/dummy || exit 0

USER=$(ps -C syslogd -o user= | head -n 1)
[ -z "${USER}" ] && USER="root" || true

set -e

cd /var/log

[I][B]# JRW Changed
# logs=$(syslogd-listfiles)
logs=$(syslogd-listfiles -s mail.log)[/B][/I]


test -n "$logs" || exit 0

for LOG in $logs
do
   if [ -s $LOG ]; then
      savelog -g adm -m 640 -u ${USER} -c 7 $LOG >/dev/null
   fi
done

# Restart syslogd
#
/etc/init.d/sysklogd reload-or-restart > /dev/null

```


Looking in my logfiles folder I now see:

```

-rw-r-----  1 syslog        adm      1560433 2008-07-28 07:19 mail.log
-rw-r-----  1 syslog        adm     12730490 2008-07-27 06:46 mail.log.0
-rw-r-----  1 syslog        adm       526966 2008-07-20 06:46 mail.log.1.gz
-rw-r-----  1 syslog        adm       193336 2008-07-17 07:09 mail.log.2.gz
-rw-r-----  1 syslog        adm       179211 2008-07-16 07:24 mail.log.3.gz
-rw-r-----  1 syslog        adm       162379 2008-07-13 06:46 mail.log.4.gz
-rw-r-----  1 syslog        adm       211572 2008-07-12 07:49 mail.log.5.gz
-rw-r-----  1 syslog        adm       224137 2008-07-11 07:10 mail.log.6.gz

```

so it looks like the change has done what I need. I can't see why mail.log.0 hasn't been compressed, but that's something for another day (unless somebody can enlighten me?)



Jim

---

### Post by MJN on 2008-07-28
> **jimwillsher said:**
> I can't see why mail.log.0 hasn't been compressed, but that's something for another day (unless somebody can enlighten me?)
 
I think you've hit the nail on the day with '*that's something for another day'*! ;)
 
I think it'll compress next time around. This allows you to see that the current and last logs in clear (non-compressed) form...
 
Mathew

---

### Post by jimwillsher on 2008-07-28
Perfect, many thanks. I'll check again next Monday :-)


Jim

---

### Post by szandor on 2008-07-31
fyi,

root@szandor:~# syslogd-listfiles --weekly
/var/log/mail.warn
/var/log/user.log
/var/log/daemon.log
/var/log/messages
/var/log/debug
/var/log/auth.log
/var/log/mail.err
/var/log/mail.log
/var/log/kern.log
/var/log/lpr.log
/var/log/mail.info

and

root@szandor:~# logrotate -d /etc/logrotate.conf 

for files in .conf and .d

---

### Post by jimwillsher on 2008-08-01
Thanks for that, that clears up my understanding of which files are rotated by which tasks.


Jim

---

