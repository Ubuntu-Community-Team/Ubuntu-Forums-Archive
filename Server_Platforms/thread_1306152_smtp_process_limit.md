---
title: "smtp process limit"
date: 2009-10-30
forum: Server Platforms
---

### Post by jonas2 on 2009-10-30
I'm having a problem increasing the Postfix 2.5 smtpd process limit to **200**. Here's what I have tried so far:

1)
/etc/postfix/main.cf:
```
default_process_limit = 200
```2)
/etc/postfix/master.cf:
```
smtp      inet  n       -       -       -       200       smtpd
```3)
/etc/postfix/master.cf:
```
smtp      inet  n       -       -       -       -       smtpd
   -o default_process_limit=200
```During heavy traffic or simulation (stress test), the number of smtpd processes reaches the default limit, whereupon the server stops accepting new connections:

$ ps -u postfix | wc -l
**101**

N.B. There are no other bottlenecks in this state (according to atop).

Error messages:
[B]warning: process /usr/lib/postfix/smtpd pid 25834 exit status 1
warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
setuid(105): Resource temporarily unavailable[/B]

/etc/security/limits.conf:
```
postfix        soft    nproc   200
postfix        hard    nproc   300
```Could any of you give me a hint, please?

---

### Post by jonas2 on 2009-10-31
Well, evidently the directives in limits.conf are completely ignored in our distribution/setup.

As a temporary solution, I placed "ulimit -u 300" in the Postfix init script.
300 smtpd processes can now be spawned, even though the process limit in master is only 200 (!).

---

