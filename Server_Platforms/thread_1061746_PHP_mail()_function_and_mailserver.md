---
title: "PHP mail() function and mailserver"
date: 2009-02-06
forum: Server Platforms
---

### Post by klaasvg on 2009-02-06
Hi all,
I have a very trivial problem but have not found a solution yet... I have Apache webserver installed under Ubututo host my own website. As a beginner with PHP, I am making the site more dynamic.
I want to include a mail form and try to use the PHP mail() function to enable the visitor to send a mail.
The mail() function however apperars to block and does  not return. Besides I have not configured the SMTP server to use so it is impossible that it will work now. Where can I configure the needed data, such as SMTP server for outgoing mail? Or do I need a program as send mail, and how can I configure this?
I hope for some hints :)
Greetz Klaas

---

### Post by hyper_ch on 2009-02-06
if you want to send it to a recipient not on that servre you will need to configure smtp somehow.

IMHO you could setup a real mailserver using postfix and then have postfix relay through a real email account of yours at an ISP. It's not difficult to setup.

Sendmail would probably be the quicker route but I have no experience with it.

---

