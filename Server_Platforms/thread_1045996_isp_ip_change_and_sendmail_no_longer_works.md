---
title: "isp/ ip change and sendmail no longer works"
date: 2009-01-21
forum: Server Platforms
---

### Post by bobginyu on 2009-01-21
I moved my computer to a new isp with a new ip and sendmail stopped sending mail.

i can telnet to port 25

resolv.conf has 192.168.1.1 listed b/c when i try 127.0.0.1 i get this error:gethostbyaddr(192.168.1.3) failed: 1

when i try to send mail via telnet everything looks fine then i get:
Jan 21 01:05:55 marty-desktop sendmail[17428]: : to=<@yahoo.com>, delay=00:01:01, xdelay=00:00:01, mailer=esmtp, pri=0, relay=e.mx.mail.yahoo.com. [216.39.53.1], dsn=5.0.0, stat=Service unavailable

Another common error im seeing:
Jan 20 19:06:16 marty-desktop sendmail[10304]: daemon MTA: problem creating SMTP socket
Jan 20 19:06:21 marty-desktop sendmail[10304]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use

all the error messages are from maillog

---

