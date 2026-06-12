---
title: "Postfix + outgoing port 25 blocked"
date: 2008-10-26
forum: Server Platforms
---

### Post by jstritar on 2008-10-26
I'm trying to setup email notifications for my RAID array, but I'm having problems since my ISP blocks outgoing port 25. Postfix times out whenever it tries to deliver the message:

> 
Oct 26 15:11:14 jstritar-desktop postfix/smtp[26600]: connect to alt2.gmail-smtp-in.l.google.com[209.85.143.114]:25: Connection timed out


Is there a way to configure postfix to use the alternative ports like 587 when trying to deliver mail?

---

### Post by rslrdx on 2008-10-26
> **jstritar said:**
> I'm trying to setup email notifications for my RAID array, but I'm having problems since my ISP blocks outgoing port 25. Postfix times out whenever it tries to deliver the message:



Is there a way to configure postfix to use the alternative ports like 587 when trying to deliver mail?

I'm no expert here, but I think you are running postfix locally, which may not be a requirement for emailing notifications, using an external mail server might be a better sollution than hosting postfix just to mail notifications. and if your port 25 is blocked, chances are you dont have a connection for "servers" (trust me... i hate this kind of crap from ISP's, I'm trying to host my own server withou paying a fortune for it) so besides changing the port, which doesnt mean the email wont be blacklisted as it comes from a dynamic ip address from an isp, but you may want to use some sort of mail relay, remember, alot of mail servers have filter to detect this kind of setup, so if you can, get it to email using an external email server.

hope it helps

here is two links that might help...


mail relay
[http://www.dyndns.com/services/mailhop/relay_howto.html](http://www.dyndns.com/services/mailhop/relay_howto.html)


change port 25 
[http://www.freebsddiary.org/postfix-transport.php](http://www.freebsddiary.org/postfix-transport.php)

---

