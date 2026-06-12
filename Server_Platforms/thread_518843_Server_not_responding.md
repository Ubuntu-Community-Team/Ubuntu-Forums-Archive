---
title: "Server not responding"
date: 2007-08-06
forum: Server Platforms
---

### Post by drinehart on 2007-08-06
I have Ubuntu Feisty installed as a file server (SAMBA), e-mail and web server.  In the past 2 months I have noticed the server stops responding from time to time and requires a reboot.  When this happens I am always interested in finding out what the cause is so I can fix it.

Is there a good step by step tutorial about how to troubleshoot an Ubuntu/Linux box based on the logs?  I'm assuming the information is found in the logs somewhere but I'm not clear about where to start or which ones would contain useful informaiton.

Any help would be appreciated.

Thanks,
Duane

---

### Post by reckless2k2 on 2007-08-06
log files in /var/log should answer some of the problems but there could be various reasons why it's not responding. it could have to do with the client and not the server. there are a lot of variables to the situation.

---

### Post by koenn on 2007-08-06
logs ar in /var/log by default. syslog and messages would be your first choice, i guess. You should also check the config files of the daemons /servers you're interested in  (samba, mail, www); they can have a specific log files specified there. 

what you're interested in ar log entries from (just before) the problem : you want to know what the server was doing when it became unresponsive. 

It may help to review /var/log/lmessages and syslog after you reboot, for any mention of recovering this or fixing problem that, which may give a clue as to what got screwed up before you rebooted

---

### Post by drinehart on 2007-08-07
The problem occured again today.  The logs seem to indicate a cron job is running right before everything freezes up:

[syslog contents]

Aug  7 16:39:01 mail1 /USR/SBIN/CRON[12517]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  7 16:58:36 mail1 syslogd 1.4.1#20ubuntu4: restart.

I noticed the problem around 4:40, tried to get on the server to see what happened (from several clients) and gave up around 5pm today (hence the reboot).

Does anyone know what this cron job above does?  Can I delete it without any problems?

Duane

---

### Post by ruibernardo on 2007-08-07
Hi,

that cron job is about php5. Do you use it on the apache server? (probably you do)

---

### Post by koenn on 2007-08-08
it says something like 

if the directory /var/lib/php5 exists,
find, then delete, the files in that directory that have had their status changd less than "maxlifetime" minutes ago. 

I don't know
* what a "change of status" is
* what '/usr/lib/php5/maxlifetime' is or does
* what the purpose of such a job could be
* whether is could be the case of the server hanging. 

but you could of course disable thecron jopb and see what happens.

---

### Post by drinehart on 2007-08-08
I disabled the cron job for now.  I also uninstalled some unneeded programs (in case they were causing some conflict) - gnome Xwindows and some minor others.

I only use the server for mail (Postfix/Dovecot), file server (Samba), web server (Apache2 w/ PHP), database (MySQL) and proxy server (Squid).  I did try setting up LTSP, Xwindows, vncserver, mono, etc.  I basically removed the stuff I don't need.

I'll keep you posted as to progress.

Duane

---

### Post by drinehart on 2007-08-16
Check the logs I saw a cron job was run at 22:17 and then there was no connectivity after than.  I rebooted the computer the next morning.

[from syslog]
Aug 11 22:17:02 mail1 /USR/SBIN/CRON[29327]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 09:29:16 mail1 syslogd 1.4.1#20ubuntu4: restart.

When I checked /etc/cron.hourly there is nothing in that directory.  

Looking at crontab I see: 

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

It appears the hourly run command is different from the daily, weekly, monthly.  Is this normal?

Fortunately I have not had any problems since Saturday.  Does anyone have an idea of what I should check next to get to the root of this problem?

Duane

---

### Post by drinehart on 2007-08-21
The server has been performing as I expected for the past 9 days.  During that time I have not had any reboots.

I recently found I had some bad blocks on an external hard drive I was using for backup, using backuppc.  Could this cause the computer to freeze?

Duane

---

