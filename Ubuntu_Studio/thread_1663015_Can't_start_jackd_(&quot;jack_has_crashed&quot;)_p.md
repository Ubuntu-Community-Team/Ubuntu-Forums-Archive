---
title: "Can't start jackd (&quot;jack has crashed&quot;) problem and my solution"
date: 2011-01-09
forum: Ubuntu Studio
---

### Post by yoni1 on 2011-01-09
If it can help anyone, or if anyone can shed any more light onto this issue:

After one of the recent dist upgrades I've been unable to start jackd after using audio on my system (e.g. from firefox), unless I reboot or logout/login again.  When trying to start jackd over alsa (using qjackctl) I get the message "jack has crashed"

After much trial and error and forum searching, I determined a way to start jackd without having to reboot or logout/login again:

rm -f /dev/shm/pulse-shm-*

After this, jackd starts and I can use it!

Use at your own risk, though, in case deleting those shared memory files might affect applications that are running.  So far I didn't notice any side affect.

---

