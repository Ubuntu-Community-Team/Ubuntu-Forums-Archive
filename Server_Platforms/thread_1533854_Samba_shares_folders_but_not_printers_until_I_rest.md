---
title: "Samba shares folders but not printers until I restart the smbd service"
date: 2010-07-18
forum: Server Platforms
---

### Post by fizgig on 2010-07-18
Just like the title states, as soon as my server comes up, I see the samba share that I made and can browse it just fine.

I don't see the printer share nor can I print to the shared printer until I execute **service smbd restart** from an ssh login.  Then I see the printer and then I can network print.

Before restarting smbd, I do check to see if it's already running and it is (two instances are running in fact).  When I restart smbd, there are still two smbd services running but they have higher PID numbers (and I can then print).

I'm running 10.04.  Anyone know how to make it all start up happily the first time without any intervention from me?

---

### Post by Morbius1 on 2010-07-18
Another "upstart" discombobulation I think. It appears the CUPS service is started in some cases after smbd has started. Maybe your answer is in this work-around:

[http://ubuntuforums.org/showthread.php?t=1477230](http://ubuntuforums.org/showthread.php?t=1477230)

BTW, there a bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141)

---

### Post by fizgig on 2010-07-18
Thanks.  That was exactly my problem.  Like the thread suggests at the end, adding a **sleep 10** just after "pre start script" in /etc/init/smbd.conf does the trick.

---

