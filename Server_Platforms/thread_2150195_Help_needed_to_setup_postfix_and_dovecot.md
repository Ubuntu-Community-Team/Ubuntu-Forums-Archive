---
title: "Help needed to setup postfix and dovecot"
date: 2013-05-31
forum: Server Platforms
---

### Post by lepidas on 2013-05-31
Hi to all, I just moved my 2 sites(Joomla and SMF) to a dedicated Ubuntu 12.04 server and I setup everything and things working pretty well except the MTA. Forum users when sending pm one to each other they don't get email notification to their inbox, admin(me) don't get email notification to inbox when new member asks for a registration and so on that member don't get his activation email to activate account on forum. With these in mind I think I need to install and configure some things in my Ubuntu server.
I searched a lot these days and the words I found are postfix and dovecot but that's all, so I need some help installing the exact right packages and configuring theme right,

thank you in advance for replies

---

### Post by lisati on 2013-05-31
Have a look here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

If you have any further questions, feel free to ask.

---

### Post by lepidas on 2013-05-31
well yes, in the postfix installation what should I choose of 3 available?

Internet Site
Internet with smarthost
Satellite system


In my Ubuntu box I have 3 websites I want the configuration to serve all my 3 domains.
I also want make configuration that when a new member subscribes my forum he gets his activation email (SMF forum and Joomla software supports SMTP service)

---

### Post by curiousofme on 2013-05-31
After spending lots of time with Dovecote and Postfix in the past, I switched to Citadel-Suite. I highly recommend it. Very easy to install, maintain, and backup. Good luck!

---

