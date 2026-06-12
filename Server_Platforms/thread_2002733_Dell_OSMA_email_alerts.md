---
title: "Dell OSMA email alerts"
date: 2012-06-13
forum: Server Platforms
---

### Post by nachtfieber on 2012-06-13
Hi Ubuntu Users,

I just spent the last two hours going through blog posts and forum entries. Unfortunately, I wasn't able to find a simple way to convince Dell's OSMA monitoring tool to send out email in case of an alert. Does anybody knowof a simple script that I can use for that purpose?

Best,
nachtfieber

---

### Post by nsnidanko on 2012-06-14
I believe you need to have IT Assistant for OSMA to send alerts. Also you can use the following:

[http://www.tachytelic.net/2010/10/dell-openmanage-server-administrator-omsa-email-alerts-for-linux/](http://www.tachytelic.net/2010/10/dell-openmanage-server-administrator-omsa-email-alerts-for-linux/)

scroll down for bash version. Just cron it and this script will parse log and email you alert.

Hope it helps.

---

