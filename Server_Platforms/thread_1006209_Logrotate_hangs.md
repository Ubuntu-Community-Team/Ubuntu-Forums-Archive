---
title: "Logrotate hangs"
date: 2008-12-09
forum: Server Platforms
---

### Post by Axier on 2008-12-09
We run Dapper LTS and recently the logrotate process has started to hang each night, consuming 80-100% CPU. Today I used apt-get to remove and then reinstall logrotate but this does not help much.

I suspect that it might be some other process that logrotate depends on that hangs, or could it be some other issue? Configuration or similar? Any ideas is welcomed.

---

### Post by stiV on 2008-12-09
with a "ps auxf" you could see what logrotate is doing (what command it is currently running) when it hangs

---

### Post by Axier on 2008-12-09
Ok, I triggered logrotate from webmin and it shows this, but is this save_log.cgi the problematic process? Usually it runs (and hangs) via crontab.
root     28072  0.0  0.1  30260  2624 ?        Ss   Sep18   1:58 /usr/bin/perl /usr/local/webmin-1.430/miniserv.pl /etc/webmi
root      4127  4.8  0.6  38452 13788 ?        S    11:12   0:00  \_ /usr/local/webmin-1.430/logrotate/save_log.cgi
root      4168 60.5  0.1   8720  2324 ?        R    11:12   0:02      \_ logrotate -f /tmp/.webmin/24701_1_save_log.cgi

---

### Post by stiV on 2008-12-09
if you can't get any output from your scripts then you could try to remove the rotating files one by one to determine which one is failing (hanging).

they should be located in /etc/logrotate.d/

are you issueing any commands? (postrotate or something similar)

---

### Post by hictio on 2008-12-09
You can also execute logrotate (on a console or terminal) on debug mode, it won't do anything, but will show you what needs to be done.

```

logrotate -d /etc/logrotate.conf 

```

Modify the path to the config file if its on another location on your box.

---

### Post by Axier on 2008-12-09
It seem to hang here or after this:
reading config info for /var/log/btmp 
and I suspect it is the last config before actually starting to rotate the logs. Can I somehow rotate one log at a time to check wheather it is a single log or another issue?

---

### Post by Axier on 2009-01-25
Bump...

I have uninstalled logrotate, I even used apt-get with the purge to get rid of it, and I also tried to reinstall gzip (since it is frequently called by logrotate). It still hangs.

I have to kill logrotate each morning (!), but I have today taken it out from crontab, but it is really not want I want to do.

It seem to hang directly after the last configuration file is read... 
... any good ideas/hints on other things to do?

---

### Post by Axier on 2009-01-28
Ok, so it is solved... there was something wrong with this file: /var/lib/logrotate/status  It was about 100M and did not work properly. I renamed it and created a new "sudo touch /var/lib/logrotate/status" and then it was done.

---

