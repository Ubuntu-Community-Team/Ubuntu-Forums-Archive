---
title: "pptp trouble(logfile and ps)"
date: 2006-04-17
forum: Server Platforms
---

### Post by wfx on 2006-04-17
Hi,
i use pptp for internet and it works.

If i do "ps -xa", i see tons of
15199 ?        S      2:04 pptp: GRE-to-PPP gateway on /dev/ptmx
15201 ?        S      0:00 pptp: GRE-to-PPP gateway on /dev/ptmx
15242 ?        S      2:00 pptp: GRE-to-PPP gateway on /dev/ptmx
15284 ?        S      0:00 pptp: GRE-to-PPP gateway on /dev/ptmx
....
28334 ?        S      0:00 pptp: GRE-to-PPP gateway on /dev/ptmx
28375 ?        S      0:03 pptp: GRE-to-PPP gateway on /dev/ptmx
28395 ?        S      0:06 pptp: GRE-to-PPP gateway on /dev/ptmx

The nex thing is the log files a very very large:
ls -lh /var/log/syslog*
-rw-r-----  1 root adm  146M 2006-04-17 19:43 /var/log/syslog
-rw-r-----  1 root adm  424M 2006-04-17 06:27 /var/log/syslog.0
-rw-r-----  1 root adm 1012K 2006-04-16 06:25 /var/log/syslog.1.gz
-rw-r-----  1 root adm  109K 2006-04-15 06:26 /var/log/syslog.2.gz
-rw-r-----  1 root adm  807K 2006-04-14 06:27 /var/log/syslog.3.gz
-rw-r-----  1 root adm  8,6K 2006-04-13 06:27 /var/log/syslog.4.gz
-rw-r-----  1 root adm  2,1M 2006-04-12 06:26 /var/log/syslog.5.gz
-rw-r-----  1 root adm  3,3M 2006-04-11 06:27 /var/log/syslog.6.gz

The syslog is full (and i mean raly full) with:
...
Apr 17 19:45:05 philoctetes pptp[19784]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[17957]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[17914]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[16933]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[16891]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[16092]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[16049]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[15242]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
Apr 17 19:45:05 philoctetes pptp[15199]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 22095 (expecting 610004)
....

This is a bad thing!
Please help, thx.

---

### Post by fdoving on 2006-04-17
Hi.

Try to set one of theese in your peers file.
[QUOTE=man pppd]
       lcp-echo-failure n
              If  this  option is given, pppd will presume the peer to be dead if n LCP echo-requests are sent without receiving a valid LCP
              echo-reply.  If this happens, pppd will terminate the connection.  Use of this  option  requires  a  non-zero  value  for  the
              lcp-echo-interval  parameter.  This option can be used to enable pppd to terminate after the physical connection has been bro-
              ken (e.g., the modem has hung up) in situations where no hardware modem control lines are available.

       lcp-echo-interval n
         If this option is given, pppd will send an LCP echo-request frame to
         the peer every  n  seconds. Normally  the  peer  should respond to
         the echo-request by sending an echo-reply.
         This option can be used with the lcp-echo-failure option to detect
         that the peer is no longer connected.

[/QUOTE]

---

### Post by wfx on 2006-04-18
thx a lot,
i have add "lcp-echo-failure 2" look's enought to fix it.

But, curios i can ping/connect any website from any desktop-system
(what is connected to the server) but not from the server itself?
But this must be some different (after a brezzy update?)
So i open a new thread

thx.

---

