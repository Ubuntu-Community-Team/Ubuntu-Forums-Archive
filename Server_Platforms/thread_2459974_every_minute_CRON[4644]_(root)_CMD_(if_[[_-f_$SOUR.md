---
title: "every minute CRON[4644]: (root) CMD (if [[ -f $SOURCE ]]; then"
date: 2021-03-30
forum: Server Platforms
---

### Post by user47112 on 2021-03-30
Hi,

i have a problem with ubuntu 16.04 server with plesk fresh installed, but in the syslog is this  every minute :

```
Mar 28 21:43:01 server CRON[5808]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:44:01 server CRON[5899]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:45:01 server CRON[5964]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:46:01 server CRON[6037]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:47:01 server CRON[6108]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:48:01 server CRON[6197]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
Mar 28 21:49:01 server CRON[6263]: (root) CMD (if [[ -f $SOURCE ]]; then cp $SOURCE $TARGET && rm $SOURCE; fi)
```



i have only this root cron job 



```
root@server:~# crontab -l
47      23      *       *       *       /usr/sbin/ntpdate -b -s 2.pool.ntp.org
```

---

### Post by TheFu on 2021-03-30
Support for 16.04 ends in a few weeks.  Best to move to a supported release since all the time synchronization stuff has changed.

I know nothing about plesk. Never touched it.

---

### Post by DuckHook on 2021-03-31
*Moved to Servers subforum for more appropriate fit.*

---

### Post by LHammonds on 2021-03-31
If you see nothing in crontab -e for the root user, it might be a script in /etc/cron.daily or /etc/cron.hourly that just loops and waits 60 seconds.

I am not familiar with that software though.

There might be a systemd service/script too.  Look in /etc/systemd/system/*.service

LHammonds

---

