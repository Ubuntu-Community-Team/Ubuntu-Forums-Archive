---
title: "Cannot find a particular cron job"
date: 2010-10-25
forum: Server Platforms
---

### Post by nucleocide on 2010-10-25
Ubuntu server 10.04:

I had webmin installed on my server, but I found it was using too many resources for what it offered, so I went ahead and uninstalled it. I'm not sure exactly which version it was, but it was the most recent version a month ago. I ran the uninstaller which ships with webmin.

Well, now everyday my root account gets the following email:

[FONT=Courier New]From [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL]  Mon Oct 18 00:42:01 2010
Return-Path: <root@DOMAIN.com>
Date: Mon, 18 Oct 2010 00:42:01 -0400
From: [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL] (Cron Daemon)
To: [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL]
Subject: Cron <root@DOMAIN> /etc/webmin/cron/tempdelete.pl #Delete Webmin temporary files
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Status: RO

/bin/sh: /etc/webmin/cron/tempdelete.pl: not found[/FONT]

I've run a grep over the entire server filesystem and cannot find a reference to this file. I've looked at all the files in /etc/cron.daily and /var/spool/cron/crontabs, and none of them execute this command. Is there someplace I'm not looking?!

---

### Post by kevin11951 on 2010-10-25
> **nucleocide said:**
> Ubuntu server 10.04:

I had webmin installed on my server, but I found it was using too many resources for what it offered, so I went ahead and uninstalled it. I'm not sure exactly which version it was, but it was the most recent version a month ago. I ran the uninstaller which ships with webmin.

Well, now everyday my root account gets the following email:

[FONT=Courier New]From [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL]  Mon Oct 18 00:42:01 2010
Return-Path: <root@DOMAIN.com>
Date: Mon, 18 Oct 2010 00:42:01 -0400
From: [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL] (Cron Daemon)
To: [EMAIL="root@DOMAIN.com"]root@DOMAIN.com[/EMAIL]
Subject: Cron <root@DOMAIN> /etc/webmin/cron/tempdelete.pl #Delete Webmin temporary files
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Status: RO

/bin/sh: /etc/webmin/cron/tempdelete.pl: not found[/FONT]

I've run a grep over the entire server filesystem and cannot find a reference to this file. I've looked at all the files in /etc/cron.daily and /var/spool/cron/crontabs, and none of them execute this command. Is there someplace I'm not looking?!

```
crontab -e
```

---

### Post by abix_adam_pl on 2010-10-26
Also check /etc/crontab file and /etc/cron.d/ directory.

Adam

---

### Post by kevin11951 on 2010-10-26
> **abix_adam_pl said:**
> Also check /etc/crontab file and /etc/cron.d/ directory.

Adam

Webmin places its cronjobs in crontab -e.

---

