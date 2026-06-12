---
title: "Sendmail not sending"
date: 2010-01-29
forum: Server Platforms
---

### Post by CharvelMan on 2010-01-29
Hi,
We are running a8.04 server for are website now for the last 6 months with no major issues. We have started to notice that when people send an email from the website, that they are not being sent. I have looked in the syslog and have pasted in the entries:


Jan 29 15:40:01 XXXXX-SERVER sm-msp-queue[7335]: o0T401sX008943: to=XXXXX, delay=11:40:00, xdelay=00:00:00, mailer=relay, pri=3271745, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Jan 29 15:40:01 XXXXX-SERVER sm-msp-queue[7335]: o0T0017D008442: to=XXXXX ctladdr=XXXXXX (1000/1000), delay=15:40:00, xdelay=00:00:00, mailer=relay, pri=4350427, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]

Any help would be greatly appricated

Thanks

---

