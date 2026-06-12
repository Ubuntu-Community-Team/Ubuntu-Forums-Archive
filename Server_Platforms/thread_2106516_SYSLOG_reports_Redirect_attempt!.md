---
title: "SYSLOG reports Redirect attempt!"
date: 2013-01-19
forum: Server Platforms
---

### Post by duesentriebchen on 2013-01-19
Hy there ladies and gentlemen :D

Checking my ```
/var/log/syslog
```i noticed these two entries.
```
Jan 11 09:01:24 HOST kernel: [2052671.020994] Redirect from 37.139.110.58 on eth0 about 37.139.96.1 ignored.
Jan 11 09:01:24 HOST kernel: [2052671.021001]   Advised path = my.ip.add -> 46.35.242.192
```Firstly i did a traceroute, and this looks "normal"
Secondly i did a check in my ```
/var/log/auth.log
``` without any queries.

A reverselookup gave me the info that these two IP's belong to boxes in the ukraine.

Can you tell me, if i have anything to worry about beeing compromised or rooted?

Thank you in advance!
Kind regards

---

### Post by craigp84 on 2013-01-19
It's a common attack attempt. Your kernel did the right thing in disallowing source routing.

---

### Post by duesentriebchen on 2013-01-19
Hy graigp84

:D my kernel just got an extracookie ;)

Can you tell me how this "common" attack attempt works?

Thank's!

---

