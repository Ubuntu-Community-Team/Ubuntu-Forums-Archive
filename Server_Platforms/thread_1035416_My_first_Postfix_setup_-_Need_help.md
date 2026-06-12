---
title: "My first Postfix setup - Need help"
date: 2009-01-09
forum: Server Platforms
---

### Post by JamesN1830 on 2009-01-09
internet -> firewall -> ubuntu in DMZ -> Exchange in Internal


Goal - I want postfix to be my relay agent of all incoming (for my domain only) and outgoing smtp only email.  Postfix will be in the DMZ while Exchange will be in my trusted local network.

Postfix info (in DMZ)...
FQDN of postfix box = MAIL-DMZ.BLACK.NET
IP = 192.168.1.5

Exchange info (in trusted)...
FQDN of Exchange box = exchange.BLACK.LOCAL
IP = 10.6.104.10

MX = mail.black.net.  



postfix is running and I can telnet 25 into it.  I can successfully get to "rcpt to: [email]postmaster@black.net[/email]", but get a "Relay Access Denied" from Postfix.


Please give this postfix/ubuntu noob some advice  :)

Thank you in adv.

---

### Post by JamesN1830 on 2009-01-09
Fixed it.  

All in he main.cf 

did not add the subnet to mynetwork

---

