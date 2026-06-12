---
title: "cron.daily not running"
date: 2015-05-02
forum: Server Platforms
---

### Post by bruce-hyatt on 2015-05-02
I have a script that runs rsync that I have placed in /etc/cron.daily and it doesn't execute. I could just edit root's crontab but I would like to figure out why I can't get the script to run the way I currently have it set up.

- The script works fine when executed from the command line
- The script is in /etc/cron.daily
- The script name does not include a period
- The script is executable
- The script belongs to root
- /etc/crontab has the default code for /etc/cron.daily

In some log (syslog, I think) cron.hourly is shown running but not cron.daily.

What could I be missing? I thought all scripts in /etc/cron.daily would run daily at the time specified in /etc/crontab. (I don't have a mail server so I don't know what the info is that I see would be sent to root's mailbox.)

TIA,
Bruce

---

### Post by Doug S on 2015-05-02
> **bruce-hyatt said:**
> In some log (syslog, I think) cron.hourly is shown running but not cron.daily.Typically, it would not show in syslog, as syslog is rotated daily (at least under default settings). However it would show in syslog.1. Example:```
doug@s15:~$ grep "cron\.daily" /var/log/syslog
doug@s15:~$ grep "cron\.daily" /var/log/syslog.1
May  2 04:25:01 s15 CRON[15049]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
doug@s15:~$
```EDIT: And actually, the entry should be near the end of the file. Example:```
doug@s15:~$ tail -3 /var/log/syslog.1
May  2 04:17:01 s15 CRON[15034]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  2 04:25:01 s15 CRON[15049]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
May  2 04:29:05 s15 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="843" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
doug@s15:~$
```

---

### Post by ajgreeny on 2015-05-02
If there are any pathways to files or folders shown in the script are they showing the full pathways without any shortcuts such as ~/ for your home?

Shortcuts like that do nor work in cron IIRC.

---

### Post by bruce-hyatt on 2015-05-02
> **ajgreeny said:**
> If there are any pathways to files or folders shown in the script are they showing the full pathways without any shortcuts such as ~/ for your home?

Shortcuts like that do nor work in cron IIRC.

No, there are only full path names in the script.

> **Doug S said:**
> However it would show in syslog.1.

Thanks. I will check there when I get home.

- Bruce

---

### Post by bruce-hyatt on 2015-05-02
Apparently the script *is* running daily. I think it was making it executable that finally got it working. Thanks for your help!

- Bruce

---

