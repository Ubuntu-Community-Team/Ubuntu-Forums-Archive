---
title: "HostnameLookups return strange ISP address"
date: 2007-09-19
forum: Server Platforms
---

### Post by simonsimoon on 2007-09-19
Ubuntu 7.04 server Apache 2.2.1 My server use

Hostnamelookups on
Order deny,allow
Deny from all
Allow from xxx.no-ip.com
Allow from yyy.no-ip.com
Allow from zzz.no-ip.com

to control who can visit the site. with setup like this, no one from [xxx yyy zzz].no-ip.com can get access.

The error.log record all access deny but using IP address only not the host name. Is this normal?

Then I change all Allow from to use IP address instead of host name. Everyone get access to the site.

I check the access.log, it did record all successful access using host name but the host name is strange. It is like

n11234123452342354.myispdomain.com
n32452345235435232.myispdomain.com

This is like the host name you get when you use nslookup. I think this is why Allow from host is not working. What should I do to let Apache2 correctly resolve the no-ip host name?

---

### Post by simonsimoon on 2007-10-04
Well waited for 2 weeks and searched for 2 weeks still cannot find an answer. Please help:confused::(:confused::(

---

