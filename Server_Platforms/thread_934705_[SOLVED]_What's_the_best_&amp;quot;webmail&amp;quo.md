---
title: "[SOLVED] What's the best &amp;quot;webmail&amp;quot; program for a ubuntu server"
date: 2008-09-30
forum: Server Platforms
---

### Post by jeantasse on 2008-09-30
I have a Postfix/Dovecot mail server, i my clients would like to have a web interface similar to yahoo.mail or hotmail.  Do anybody have an idea of a good "webmail" program with the best reputation to work with Ubuntu

Ubuntu server 32 bits 8.04.1

---

### Post by Cybergod on 2008-09-30
> **jeantasse said:**
> I have a Postfix/Dovecot mail server, i my clients would like to have a web interface similar to yahoo.mail or hotmail.  Do anybody have an idea of a good "webmail" program with the best reputation to work with Ubuntu

Ubuntu server 32 bits 8.04.1

I really like [SquirrelMail]("http://www.squirrelmail.org/"):D

---

### Post by Xipher on 2008-10-01
I have found [RoundCube]("http://roundcube.net") to be quiet nice.

---

### Post by devonps on 2008-10-01
I use [[COLOR="Blue"]_Citadel_[/COLOR]]("http://www.citadel.org"), to provide an all round email solution.

Where as some people will cite Zimbra as an alternative - but I've not installed that.

It really depends on what you and/or your customers want from their email - ask them?

---

### Post by jeantasse on 2008-10-01
What they want is simple, they are not always on their pc so where ever they are, they want to be able to check there e-mail.  But no one ask for anything specific.  I looked at Citadel and it seems very professionnal,the one i found also was squirrelmail, any preference between the two?  Citadel looks more complete, do i have to reconfigure anything, install spam assassin before or after?

P.S. Hi to the people of Nottingham!!!

---

### Post by hyper_ch on 2008-10-01
Squirrelmail is very easy to setup and has quite a few plugins.
Horde is also nice...
Citadel, if I'm not mistaken, is a completely different league that provides it's own mailserver....

---

### Post by jeantasse on 2008-10-01
Thank you hyper_ch, its true as i was reading, i don't want to reinstall everything, or spend to much time in testing bla bla so my choice will be Squirellmail.  Did you ever install it?  They where suggesting to create the folder attach in /tmp, what do you think of that?

---

### Post by hyper_ch on 2008-10-01
I run sqwebmail on my server... /tmp folder is not good for attachments... it's good for temporary uploads that will then be moved...

---

### Post by HermanAB on 2008-10-01
Citadel is a complete mail system.  It takes about 20 minutes to install and another twenty or so to add spam assassin and clamav.

However, if you already have a working system with a gazillion users and gigabytes of email, then I would suggest just to add roundcube to it.

Cheers,

Herman

---

### Post by jeantasse on 2008-10-01
Thanks for everybody's help, i really appreciate.!!!!!!!!!!!!!


JF

---

### Post by windependence on 2008-10-02
I's also like to suggest Zinbra for a complete solution.

-Tim

---

