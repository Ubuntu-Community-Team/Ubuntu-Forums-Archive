---
title: "Martian Source Flodding Syslog"
date: 2016-05-27
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-05-27
I'm running Ubuntu server 14.04 and I'd like to stop logging martian source messages as they are flodding the syslog, but the settings I've tried have no impact and leave the logging intact:

rc.local:
/bin/echo "0" > /proc/sys/net/ipv4/conf/all/log_martians 

No change to the logfile.

and in sysctl.conf:
net.ipv4.conf.all.log_martians = 0
net.ipv4.conf.default.log_martians = 0


No change to the logfile.
Martian source messages are from network devices searching for a printer which is turned off 99% of the time.

I was able to remove the logging of Martian Source in Shorewall.conf

Resolved.

---

