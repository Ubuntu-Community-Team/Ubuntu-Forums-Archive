---
title: "Postfix/Dovecot Configuration Syslog/Throttling Error"
date: 2007-06-03
forum: Server Platforms
---

### Post by CaptainMorgan on 2007-06-03
*********** alternative solution found ************

*But just in case anyone still has this error:*

When a self test is attempted after this setup as it is now, through **telnet localhost 25** it connects and then hangs. If I attempt **EHLO localhost** it continues to hang. Upon reload and/or restart of postfix and/or dovecot the only signs of errors are within **syslog** which I tailed. Syslog states that the reload and restarts were successful. Soon after and repeatedly I will receive this from syslog:

[B]Jun  3 03:34:59 Captains postfix/smtpd[26335]: fatal: open database /etc/aliases.db: No such file or directory
Jun  3 03:35:00 Captains postfix/master[5426]: warning: process /usr/lib/postfix/smtpd pid 26335 exit status 1
Jun  3 03:35:00 Captains postfix/master[5426]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling[/B]

---

### Post by CaptainMorgan on 2007-06-05
Evidently, all I had to do concerning this syslog error was:
**sudo newaliases**

Which will enable postfix to find an aliases.db. Now, I am able to send and receive mail **locally**. I do not as of yet know why I am unable to send and receive globally. 

-Capt

---

### Post by CaptainMorgan on 2007-06-06
Enough of this crap. I just happened to stumble across a perl module that uses sendmail differently and its install was a piece of a cake. 

-Capt

---

