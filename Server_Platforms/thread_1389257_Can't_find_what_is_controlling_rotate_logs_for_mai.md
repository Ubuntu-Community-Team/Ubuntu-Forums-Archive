---
title: "Can't find what is controlling rotate logs for mail"
date: 2010-01-24
forum: Server Platforms
---

### Post by volkswagner on 2010-01-24
I am trying to replicate my logrotate scheme on my new VPS.  I have been running Server 8.04 locally, built with various how-to instructions...starting with the "perfect server" and Flurdy's Postfix/courier/squirrelmail.  I went back through the how-to's yet I did not see any reference to setting up logrotate or similar.

I don't see any information in logrotate nor cron, referencing the rotation of mail logs, yet the do get rotated and compressed.

Any hints where else the script/command may be located?

TIA

---

### Post by pcanham on 2010-01-24
logrotate is most probably doing the log rotation for you.

try having a look at the following config file

sudo vi /etc/logrotate.d/rsyslog

---

### Post by volkswagner on 2010-01-24
Thanks for the suggestion.  I have checked the usual logrotate and cron.

I have no reference for mail log in:

```
ls /etc/logrotate.d
apache2  aptitude       clamav-freshclam  mysql-server  samba      wpa_action
apt      clamav-daemon  dpkg              ppp           shorewall

```

```
ls /etc/cron.d
amavisd-new  php5
```

There is also no mention in cron.daily, cron.weekl, etc., nor in crontab itself.

---

