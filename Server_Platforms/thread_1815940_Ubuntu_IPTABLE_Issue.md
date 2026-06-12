---
title: "Ubuntu IPTABLE Issue"
date: 2011-08-01
forum: Server Platforms
---

### Post by ringding on 2011-08-01
We have a Machine running Ubuntu Desktop which acts as a Gateway for our servers.

It runs IPTables to allow access on certain ports for VPN, HTTP etc and works absolutely fine.

However, every week or two, it seems to stop traffic. You can't see our websites, mailserver or or VPN. You can ping servers on their IP addresses but the websites will not load.

It works fine after a reboot, but having done further tests, it seems that simply sudo bashing the saved IPtable restores services again.

Someone suggested putting a cron job on it to restart the IPtables every night, but tbh I would rather understand why this would even happen in the first place.

It has been running for around 18 months, the first 12 months were fine with no dropouts at all, but now it seems to be getting more common.

Can anyone help?

---

