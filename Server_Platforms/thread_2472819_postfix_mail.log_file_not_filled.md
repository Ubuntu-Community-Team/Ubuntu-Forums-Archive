---
title: "postfix mail.log file not filled"
date: 2022-03-14
forum: Server Platforms
---

### Post by baze-alt on 2022-03-14
Hello,

I really do not know if it is the correct fprum to post but I hope some help by someone or to redirect me to the correct one.

I am working on an Ubuntu distribution 20.04.1 LTS and running Postfix 3.4.13 version on it. Since some days the mail.log file does not fill even if the service is still working.
I applied a lot of solution described over the Internet and the issue still persists.
- Adding a path in mallog_file in postconf
- Restarting syslog

The only to make it works again until 00:00 is to make these command lines
postfix stop
touch /var/log/mail.log
chown syslog:adm /var/log/mail.log
service syslog restart
postfix start

Every day @00:00 a new mail.log is created by root account. making a shell with the 4 previous command wad an alternative but does not seem to work.

I do not know if it is a Postfix or Ubuntu unexpected behaviour, that is why I am trying to get help.

Regards

---

### Post by TheFu on 2022-03-14
I have an email gateway running the same postfix on 20.04 too.  No seeing the same issue. The system here has been working about 4 months when I moved off debian to ubuntu for the gateway.
```
-rw-r----- 1 syslog adm  126056 Mar 14 16:46 mail.log
-rw-r----- 1 syslog adm 1165418 Mar 12 23:43 mail.log.1
-rw-r----- 1 syslog adm  117483 Mar  5 23:49 mail.log.2.gz
-rw-r----- 1 syslog adm   91830 Feb 27 00:00 mail.log.3.gz
-rw-r----- 1 syslog adm  140482 Feb 19 23:55 mail.log.4.gz
```

I patched the box on Saturday morning, so it is up to date. I patch it weekly.

I see no specific reference to mail.log in my postfix configs anywhere. I think they are just writing to rsyslogd and that process is choosing where to place the mail logs. The 50-default.conf file has the mail.* line which points to /var/log/mail.log

But I could be wrong. Things could have changed under systemd and I don't claim to know what is happening between journalctl and rsyslogd.

Update: all my Unix-like OSes have postfix to send daily reports to a central account.  Only the email gateway is allowed to send/receive from the internet.  Our main email/communications server isn't on the internet and it uses the Zimbra Suite (which also uses postfix).  On a system with lots of static websites and a reverse proxy for other websites, 
```
$ ll mail.log*
-rw-r----- 1 syslog adm     0 Mar 14 06:25 mail.log
-rw-r----- 1 syslog adm 23006 Mar 14 06:25 mail.log.1
-rw-r----- 1 syslog adm  2595 Mar  6 06:25 mail.log.2.gz
-rw-r----- 1 syslog adm  3208 Feb 28 06:25 mail.log.3.gz
-rw-r----- 1 syslog adm  2428 Feb 20 06:25 mail.log.4.gz
```
The default rsyslog settings appear to keep 5 logs and rotate weekly, as spelled out in the /etc/rsyslog.d/50-default.conf config file (mentioned above).

There's mention of restarting rsyslogd in the rsyslogd config files. Postfix seems to run inside a chroot by default. On all the satellite systems, all I did was install the packages and answer the TUI questions. I've never touched syslog or postscript settings on those send-only systems. The only key answer I recall in the TUI (dpkg-reconfigure) was the relay host. For that, I enter the IP address of our Zimbra server.  I do setup the /etc/aliases file and run **newaliases** to ensure the expected local accounts forward all their email to a valid Zimbra mailbox for review. That's been required for all MTAs as long as I've been an admin - nearly 3 decades now.

---

### Post by rsteinmetz70112 on 2022-03-14
I have a 20.04 computer with postfix that handles our outgoing mail from that location. It's pretty much a standalone default set-up except it will not accept incoming mail and will only send mail from our LAN addresses. In /var/log I'm seeing 4 sets of mail logs  mail.err, mail.info, mail.warn and mail.log. They all rotate pretty much like TheFu's example above.

---

### Post by Gibbs on 2022-03-15
Is anything being logged to the journal? ```
journalctl -f -u postfix@-.service
```

Check if you have a log rotation rule under /etc/logrotate.d/ - it might be doing something funky in pre/post rotate.

---

### Post by baze-alt on 2022-03-17
Hello,

Thank you for the answers, the system ran correctly during 1 year without any issue and the log stopped to be filled.

That is why I do not know if it is an issue with Postfix or Ubuntu.

Regards

---

### Post by TheFu on 2022-03-17
journald has a config file which can be configured to limit the number and size of logs retained.
**man journald.conf**
has all the details.

---

### Post by ready-don on 2022-08-26
It looks as though I've got the same problem with postfix suddenly stopping writing logs to /var/log/mail.log.
I've got two servers running on raspberry pi 4's and both stopped loging to /var/log/mail.log on the 16th August after I did a routine update with webmin.
I've checked the postfix and rsyslog files and nothing seems to have changed with the configuration.
The postfix logs are now all being written to the journal and can be seen using > journalctl -f -u [EMAIL="postfix@-.servic"]postfix@-.servic[/EMAIL]e
I'm stumped as to how I can get the /var/log/mail.log working again as fail2ban is configured to use this. Any ideas as to what could have changed?
Postfix is currently 3.4.13-0ubuntu1.2 and rsyslog is 8.2001.0-1ubuntu1.3

-rw-r----- 1 syslog adm        0 Aug 20 11:23 mail.err
-rw-r----- 1 syslog adm     2946 Aug 16 00:50 mail.err.1
-rw-r----- 1 syslog adm     1700 Aug 13 22:48 mail.err.2.gz
-rw-r----- 1 syslog adm     1869 Aug  6 00:50 mail.err.3.gz
-rw-r----- 1 syslog adm     1553 Jul 30 20:36 mail.err.4.gz
-rw-r----- 1 syslog adm        0 Aug 20 11:23 mail.log
-rw-r----- 1 syslog adm  4452935 Aug 16 00:57 mail.log.1
-rw-r----- 1 syslog adm  1573079 Aug 13 23:59 mail.log.2.gz
-rw-r----- 1 syslog adm  1381983 Aug  6 23:59 mail.log.3.gz
-rw-r----- 1 syslog adm  1006682 Jul 30 23:59 mail.log.4.gz

---

