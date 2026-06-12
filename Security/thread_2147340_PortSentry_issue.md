---
title: "PortSentry issue"
date: 2013-05-21
forum: Security
---

### Post by Grand Puba on 2013-05-21
Hi,

I have portsentry installed on my Ubuntu 13.04 machine. I hardened my ubuntu install from day 0, using security guides on this forum (bodhi, etc).
Scanning my IP with NMap yielded no open ports - I did this several times on different dates with the same result when on the 18th of May I found out that NMap shows the following ports open:

Discovered open port 111/tcp on 10.0.0.3
Discovered open port 143/tcp on 10.0.0.3
Discovered open port 1/tcp on 10.0.0.3
Discovered open port 79/tcp on 10.0.0.3
Discovered open port 119/tcp on 10.0.0.3
Discovered open port 1080/tcp on 10.0.0.3
Discovered open port 12345/tcp on 10.0.0.3
Discovered open port 1524/tcp on 10.0.0.3
Discovered open port 32771/tcp on 10.0.0.3
Discovered open port 32774/tcp on 10.0.0.3
Discovered open port 2000/tcp on 10.0.0.3
Discovered open port 32773/tcp on 10.0.0.3
Discovered open port 31337/tcp on 10.0.0.3
Discovered open port 6667/tcp on 10.0.0.3
Discovered open port 32772/tcp on 10.0.0.3

Further checks showed that portsentry is listening on these ports. I did all the forensics that are recommended online, checked all the logs but there is nothing special.
However, portsentry.history file shows this single line:

1368885418 - 05/18/2013 16:56:58 Host: 10.0.0.3/10.0.0.3 Port: 1 TCP Blocked

On that date and time I was browsing a hacking site that had some info I was looking for (I am trying to learn a bit about penetration testing).
Apparently I was scanned / attacked but there is nothing suspicious on the logs, there is nothing suspicious or out of the ordinary on "netstat watch -anlp", etc. all is normal except of these ports that portsentry keeps opening. I assume there is a reason for this and I am requesting help in figuring out what is going on.

Thanks.

P.S
I might add that scanning my Ubuntu pc with NMap from a different computer (my laptop) doesn't show any open ports. Scanning from within Ubuntu shows these ports as open.

---

### Post by unspawn on 2013-05-21
Psionic PortSentry was a set of tools created the previous millennium. PortSentry was acquired by Cisco in 2002 and last updated on Sourceforge in 2003. Cisco does not support PortSentry. Subsequently any article, documentation or web log post recent or old referring to PortSentry should be considered misguided, misinformed, suspect, ignorant, outdated, deprecated, obsolete (well, you get the point ;-p). If you want pro-active measures please consider using up to date SW like Snort inline, Snort plus third party apps, fail2ban, etc, etc or any equivalents instead.

---

### Post by Grand Puba on 2013-05-22
Ok... I understand. Uninstalled it and all ports are now closed.
Thanks!

---

