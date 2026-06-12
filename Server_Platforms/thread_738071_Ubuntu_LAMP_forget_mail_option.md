---
title: "Ubuntu LAMP forget mail option"
date: 2008-03-28
forum: Server Platforms
---

### Post by Mike V on 2008-03-28
Hi all, 

Background:
I need to have a DB in production area, the must be able to enter data and the master user must be able to run some querys against that data, also I want to be notified by email every Friday about the production of every person/user.

Current:
I installed an Ubuntu LAMP server but without mail server, I already did some php pages and the DB is up and running, the thing is that I ain't able to send email because I didn't install a mail server.

Problem:
How do I send/what I need to install, to send emails (not need to receive mails and it's better that way) through php, I check this thread: 

[http://ubuntuforums.org/showthread.php?t=308453](http://ubuntuforums.org/showthread.php?t=308453)

but doesn't seem to be what I need, I also read about exim in help.ubuntu but I'm not sure if that will help.

Thanks in advance for your support.

---

### Post by Poleh on 2008-03-29
well, in order to send mails you WILL need access to a smtp mail server. You can install postfix/sendmail locally, or if you already have a smtp mail server in your organisation you can feed its details to your PHP configuration and you should be able to send mail ok.

---

