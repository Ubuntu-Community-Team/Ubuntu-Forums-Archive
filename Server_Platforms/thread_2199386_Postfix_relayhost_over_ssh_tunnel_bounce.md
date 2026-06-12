---
title: "Postfix relayhost over ssh tunnel bounce"
date: 2014-01-13
forum: Server Platforms
---

### Post by jose.dr.g on 2014-01-13
HI,

I'm using postfix 2.10.2 on ubuntu.  I relay my mail to one of my servers when I'm developing on my local machine.  

On my local machine in main.cf i have

smtpd_relay_restrictions = mynetworks, permit_mynetworks, permit_sasl_authenticated
relayhost=[127.0.0.1]:2526

Then on my local machine I create a tunnel

ssh -N -L 2526:localhost:25 [EMAIL="cqadmin@s1.example.com"]cqadmin@s1.example.com[/EMAIL]


When I do this, the mail bounces.  Postfox on my localhost doens't even connect to the remove postfix server.  Any ideas?

Nov 25 20:55:17 endosymbiont postfix/pickup[9632]: 99210A4C11: uid=33 from=<admin@example.com> 
Nov 25 20:55:17 endosymbiont postfix/cleanup[9642]: 99210A4C11: message-id=<20131126045517.99210A4C11@endosymbiont> 
Nov 25 20:55:17 endosymbiont postfix/qmgr[9633]: 99210A4C11: from=<admin@example.com>, size=32069, nrcpt=1 (queue active) 
Nov 25 20:55:17 endosymbiont postfix/error[9644]: 99210A4C11:  to=<example@gmail.com>, relay=none, delay=0.03,  delays=0.02/0.01/0/0.01, dsn=5.0.0, status=bounced ([127.0.0.1]:2526) 
Nov 25 20:55:17 endosymbiont postfix/cleanup[9642]: 9F89CA4C12: message-id=<20131126045517.9F89CA4C12@endosymbiont> 
Nov 25 20:55:17 endosymbiont postfix/qmgr[9633]: 9F89CA4C12: from=<>, size=33807, nrcpt=1 (queue active) 
Nov 25 20:55:17 endosymbiont postfix/bounce[9645]: 99210A4C11: sender non-delivery notification: 9F89CA4C12 
Nov 25 20:55:17 endosymbiont postfix/qmgr[9633]: 99210A4C11: removed 
Nov 25 20:55:17 endosymbiont postfix/error[9644]: 9F89CA4C12:  to=<admin@example.com>, relay=none, delay=0.02,  delays=0.01/0.01/0/0, dsn=5.0.0, status=bounced ([127.0.0.1]:2526) Nov  25 20:55:17 endosymbiont postfix/qmgr[9633]: 9F89CA4C12: removed

---

### Post by SeijiSensei on 2014-01-14
I'd consider setting up a simple, shared-key point-to-point OpenVPN tunnel between the two machines.  See [this document](http://openvpn.net/static.html) for details.

---

