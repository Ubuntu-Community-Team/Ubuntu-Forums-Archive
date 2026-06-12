---
title: "Server log question"
date: 2010-12-01
forum: Server Platforms
---

### Post by grimm08 on 2010-12-01
I was checking my logs on my server Sunday the 29th of November when I noticed my logs were deleted.

My first reaction was maybe I was hacked, but considering no new accounts, passwords or file ownerships were modified or added as far as I can tell I can safely assume I was not hacked.

My question is does Ubuntu clear out the its logs from time to time, thanks for your help?

---

### Post by CharlesA on 2010-12-01
Yes, the logs are archived off and on.

This is what mine looks like:

```
-rw-r----- 1 syslog adm 364000 2010-12-01 08:45 /var/log/auth.log
-rw-r----- 1 syslog adm 168861 2010-11-28 06:25 /var/log/auth.log.1
-rw-r----- 1 syslog adm  14938 2010-11-21 06:25 /var/log/auth.log.2.gz
-rw-r----- 1 syslog adm  10872 2010-11-14 06:39 /var/log/auth.log.3.gz
-rw-r----- 1 syslog adm   9625 2010-11-07 06:25 /var/log/auth.log.4.gz

```

---

### Post by SeijiSensei on 2010-12-01
Log rotations are managed in /etc/logrotate.conf and /etc/logrotate.d/.  That directory enables package installers to drop service-specific files into the configuration.  See "man logrotate" for details on the syntax of these files.  It's pretty straightforward.  logrotate runs each day via /etc/cron.daily.

---

