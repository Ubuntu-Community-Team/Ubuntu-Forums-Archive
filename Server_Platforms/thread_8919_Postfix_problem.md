---
title: "Postfix problem"
date: 2004-12-22
forum: Server Platforms
---

### Post by lmckevitt on 2004-12-22
Hi, folks,
I'm really enjoying my new Ubuntu install, but I'm having a problem with Postfix recieving mail.  My setup: I have a real domain from Dyndns (the freebie), and a Linksys router that routs the mail fine.  I have an XP box and the Ubuntu box behind it.  I've installed WorkgroupMail on the XP box to act as a mail server until I can get Postfix running.  Whenever I route mail to WorkgroupMail, I get the email fine.  The only errors that I see in my logs are " warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ".  Could this be the problem?  Thanks.

---

### Post by cmize on 2005-01-03
Just copy /etc/resolv.conf to /var/spool/postfix/etc/resolv.conf and restart postfix.

---

