---
title: "Setup email and domain name?"
date: 2013-05-19
forum: Server Platforms
---

### Post by caleb12134 on 2013-05-19
Can someone please tell me how  to setup my email server.  sendmail is installed and i want to setup RoundCube. I have it in my apache web server and installed i just dont know what  the POP3/IMAP/SMTP details are??? Also how do i set the domain to my server to be "www.balnazzar.com"?? would love any help and appreciate it :D as you can tell im a basic linux user :D Thanks!!!

---

### Post by HermanAB on 2013-05-20
Howdy,

I'd recommend against Sendmail - I actually used it about 100 years ago.  What you got is probably Postfix, which has a Sendmail compatibility program.  So go to the [http://www.postfix.org](http://www.postfix.org) web site and start reading.  Since it is your first time, it will take you about 2 weeks to install it and get it to work.  

If you don't have 2 weeks of your life to dedicate to Postfix, then install Citadel.  That one will take about 20 minutes and it is in the repos.

---

### Post by CharlesA on 2013-05-20
+1 to postfix. I've been using postfix and dovecot for my mail server, but Citadel would work fine.

I've also used iRedMail in the past, but I'm not really fond of the way they handle setting up roundcube.

---

