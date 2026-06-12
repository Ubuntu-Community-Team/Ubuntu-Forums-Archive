---
title: "iptables logs the same MAC address over and over..."
date: 2009-05-20
forum: Server Platforms
---

### Post by sickdude on 2009-05-20
Hi all,

Well lets get straight to the point.

I use the touchterm app for iPhone to monitor my server while on the road. But for secure reasons i have port 22 open for some ip addresses (work, home, school) which is ok when i am on a wifi connection in these places but i wanted to improve my iptables skills and add a MAC address filter.

So i used the syslog, in which iptables logs, to check what the MAC address of my iPhone was while its on the 3G connection.

Well it logs the most crazy MAC address i have ever seen in my sysadmin lifetime, 00:XX:48:XX:2d:XX:00:XX:23:XX:00:XX:08:XX. The XX's are my doing for secure reasons, go figure :-P

This is only the tip of the iceberg, this MAC is logged for every entry in all my logs. Since i never was intrested in this kind of info i never noticed this but now i really want to know what kind of crazy problem this is. Does anybody have this problem? Why isnt my log as acurate as it should be? What is this wierd kernel thinking?

uname -a
Linux XXXX 2.6.24-23-server #1 SMP Wed Apr 1 22:22:14 UTC 2009 i686 GNU/Linux

iptables -V
iptables v1.3.8

---

