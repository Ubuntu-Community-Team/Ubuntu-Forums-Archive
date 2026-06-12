---
title: "cron is filling up my logs"
date: 2011-08-09
forum: Server Platforms
---

### Post by benkuhn on 2011-08-09
I am using my ubuntu server as my home router.  Everything is working as expected with one exception.  My DSL modem is a POS and every now and again it looses connection to the router.  Sometimes it needs to be reset and sometimes it does not.  Either way, when this happens my ubuntu server needs to reacquire an IP from my ISP.  If it screws up when I'm at home it's no big deal, but if it happens when I'm not around my housemates have taken to hitting the reset switch on the server.  I'm not a big fan of this so I wrote a script to ping my ISP's gateway.  If it's unavailable it bounces the eth0 interface and tries to get an IP.  I am running this script every couple of minutes in a cron job.  Now I'm getting syslog entries like ```
Aug  9 20:31:01 portal CRON[9602]: (root) CMD (/opt/ChkAndFixNetwork.sh)
``` every few minutes.  This is annoying and makes the logs useless for troubleshooting.  I have tried adding ```
# Log cron stuff
cron.*                                                  /var/log/cron
``` to my /etc/rsyslog.conf but rsyslog is still dumping these messages to /var/log/syslog.  /var/log/cron exists and there are no errors when restarting rsyslog.  What am I doing wrong?

---

### Post by cj13579 on 2011-08-10
Try using:

```
cron.err               /var/log/cron.log
```

This will log errors, critcals and alerts only.

You could also take a look at [http://www.unix.com/man-page/Linux/5/rsyslog.conf/](http://www.unix.com/man-page/Linux/5/rsyslog.conf/) for all the different logging levels you can set.

---

