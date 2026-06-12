---
title: "RKhunter not sending daily report"
date: 2014-11-06
forum: Server Platforms
---

### Post by Lappert on 2014-11-06
For a number of years, I've run a server with Debian Wheezy. Every morning it runs cron.daily and sends a Rkhunter report. I believe the email directive is in /etc/rkhunter.conf, but the line reads:

MAIL_ON_WARNING=""

so I don't know how it knows to send the report to root, but it does.

So I recently set up a desktop with Ubuntu server with KDE desktop (essentially Kubuntu) and also want the rkhunter to mail the daily report.

The rkhunter.conf file also reads MAIL_ON_WARNING=""
and I can't find anywhere else that might prompt the daily report to be sent.

One difference might be that on the server, we're running Postfix, while that's missing from the desktop. There is no domain associated with the desktop. (dynamic IP of 192.168.1.XXX) For mail we log into the server with POP accounts.

Help!!!

---

### Post by howefield on 2014-11-06
Thread moved to "*Server Platforms*" forum.

---

### Post by Lappert on 2014-11-06
Thanks, but the issue is with the desktop. It's not a server. I only used Ubuntu server in order to set up RAID. Otherwise it's a desktop ... no Apache, no Postfix, nothing like that. I only mention our real server for comparison purposes.

---

