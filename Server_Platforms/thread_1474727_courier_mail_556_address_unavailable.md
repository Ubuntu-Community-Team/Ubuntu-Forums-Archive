---
title: "courier mail 556 address unavailable"
date: 2010-05-06
forum: Server Platforms
---

### Post by hall_monty on 2010-05-06
My courier server cannot recieve mail.  My freebsd installation has worked for quite some time w/o problems.  I'm using ubuntu as a replacement and have tried using the same settings from my previous server.  I keep getting the following error and am unable to find a solution.  Any suggestions appreciated.

Monty
courieresmtpd: error,relay=::1,from=<XXXX>,to=<YYY>: 556 Address unavailable.

---

### Post by hall_monty on 2010-05-06
It works after chaning ownership of /var/run/courier/authdaemon to daemon:daemon.  I'm not sure if this is safe.  If anybody can point me to specific documentation that address this (if this the correct thing to do), would appreciate this.  Out of the box, freebsd didn't have a problem.  I don't know of ubuntu did this on purpose for safety reasons or not.

---

