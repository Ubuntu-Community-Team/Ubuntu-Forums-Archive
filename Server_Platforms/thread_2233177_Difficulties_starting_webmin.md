---
title: "Difficulties starting webmin"
date: 2014-07-07
forum: Server Platforms
---

### Post by AussieGuy on 2014-07-07
So yesterday I got a new VPS running Ubuntu 14.04 set up; the hosting company provided a "minimal" installation; so I added on apache2 and a couple of other things, including webmin.  And yesterday (from home) webmin was starting fine.  But today (from work) it just won't.  I've rebooted the server, and checked that apache2 is running (because another service I installed is working); and also restarted webmin with "service webmin restart".  However, I simply can't access it remotely.  I've tried with both http and https; the browser just says "Connecting..." with no result.  Of course I can manage without webmin - I could do all my sysadmin from a terminal and an ssh login; but on the other hand I would like to use webmin if I could.  I wonder if my work has blocked off access to port 10000 on external machines?  In which case - what other ports can I use?

Thanks,
-A.

---

### Post by Habitual on 2014-07-07
```
telnet <WA_IP> 10000
``` see if it 'answers'.

---

