---
title: "Server time/date is wrong even if ntpd is running"
date: 2011-03-20
forum: Server Platforms
---

### Post by andy80 on 2011-03-20
Hi all,

I've an Ubuntu Server installation (Karmic) on a VPS hosted in Germany. 

My activity is currently based in Italy and I've set the timezone to Europe/Rome, using: **dpkg-reconfigure tzdata**

If I run date on my home PC I get:

```
andrea@centurion:~$ date
dom 20 mar 2011, 21.09.40, CET
```

If I run it on my server, I get:

```
root@wifi:~# date
Mon Mar 21 20:26:56 CET 2011
```

that is of course wrong. I've installed and configured ntpd on the Ubuntu server, but it looks like it's not working correctly.

How can I fix this?

---

### Post by falko on 2011-03-20
You might have to reboot the system after dpkg-reconfigure tzdata.

---

### Post by BkkBonanza on 2011-03-21
Check the log for errors from ntpd. Make sure a firewall isn't blocking ntpd - that sometimes is the problem.

Try **ntpdate** command manually and see what happens, errors or successful update.

sudo ntpdate ntp.ubuntu.com


I actually prefer to use ntpdate in my cron.hourly or cron.daily as it means one less daemon running, and I don't need an ntp server for my network.

---

### Post by SeijiSensei on 2011-03-21
ntpd has some safety limits based on the size of the discrepancy between local time and network time.  If the discrepancy is too big, ntpd won't update the time.

Try setting the time manually as close as you can to the correct time, then start ntpd.  You should be fine after that.

---

