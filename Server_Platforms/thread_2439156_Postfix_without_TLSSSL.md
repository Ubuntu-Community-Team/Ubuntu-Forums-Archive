---
title: "Postfix without TLS/SSL?"
date: 2020-03-23
forum: Server Platforms
---

### Post by default3 on 2020-03-23
Version: Ubuntu Server 16.04

I installed Postfix to send mail from my Ubuntu Server to my local relay server. My local relay server only supports plaintext SMTP authentication on port 25. I know it's not really secure but it's what I have to work with for the moment.
 Is it possible to have Postfix authenticating to the local relay server without encryption using plain text SMTP authentication on port 25? I've read many, many guides on how to use Postfix in combination with an external mail relay but all use encryption.
For example, this: [https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/](https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/)

I tried setting options below in main.cf and many other things but I can't get it to work.
smtp_use_tls = no
smtpd_use_tls = no
smtp_sasl_security_options =

I also tried ssmtp which worked to some extend but it has some limitations so I need Postfix instead. Sendmail is too complex for me.

---

### Post by wildmanne39 on 2020-03-23
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

