---
title: "I am moving from MDaemon to Postfix"
date: 2008-08-07
forum: Server Platforms
---

### Post by @ngkor on 2008-08-07
Hi everyone,

I'm new to Postfix, I plan to run Postfix on Ubuntu Server 8.04 for my branch office. Below are what we have, what we need and problem we face.


Here what we currently have:
===========================
My Head Office running Exim 4 as MTA, so all users have to connect to head office to receive their email.

At my branch office we use MDaemon to handle local email and download email from Head Office mail server for our local users. Every user at my branch office has their email account on both MDaemon and Exim (the same email account), I config MDaemon to download email every 15mn from Exim for each user account by using MultiPOP. So our local users send and receive their email via MDaemon.


And here what we need:
======================
I would like to replace MDaemon with Postfix for my branch office, and now I am facing a problem when my local user in branch office try to send email to head office user. Postfix will reject the email with "Unknown Virtual User". I use virtual mailbox domain because my user don't need any linux account.

This problem can be handle by MDaemon with the "Unknown Mail" option, mean MDaemon will forward unknown email address to any other SMTP server (yes, I set it to my head office mail server).

Anyone please advice me how can I configure Postfix to forward Unknown email address to another SMTP server?

Thanks

---

### Post by dasche on 2011-05-07
u can use /etc/aliases file in linux for this purpose.

---

