---
title: "Where is cron.log"
date: 2008-07-17
forum: Server Platforms
---

### Post by satimis on 2008-07-17
Hi folks,


Ubuntu LAMP 6.06 amd64


I can't find cron.log


$ locate cron.log
No printout


$ ps aux | grep cron```

root      8335  0.0  0.0  11424   884 ?        Ss   19:02   0:00 /usr/sbin/cron
satimis   8431  0.0  0.0   3944   900 pts/1    R+   19:10   0:00 grep cron

```


Please advise.  TIA


B.R.
satimis

---

### Post by MJN on 2008-07-17
It logs via Syslog - see entries in /var/log/syslog (with [CRON] identifiers).
 
Mathew

---

