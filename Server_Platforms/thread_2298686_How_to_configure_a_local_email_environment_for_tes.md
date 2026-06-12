---
title: "How to configure a local email environment for testing purposes?"
date: 2015-10-13
forum: Server Platforms
---

### Post by lordscales91 on 2015-10-13
All the tutorials that I've seen so far explain how to configure Postfix/Sendmail to actually send emails to real addresses, that means dealing with SSL certificates and a lot of complicated stuff, I don't want that (yet), I just want to send and receive email on localhost that's all. More specifically I'm developing a web application and I would like to test the activation of accounts by email. Is there any easy solution available?

---

### Post by SeijiSensei on 2015-10-13
Installing [Postfix]("https://help.ubuntu.com/lts/serverguide/postfix.html") and [Dovecot]("https://help.ubuntu.com/community/Dovecot") should work with little extra configuration.  Have the web application send mail to username@localhost using your own username.

---

### Post by lordscales91 on 2015-10-13
> **SeijiSensei said:**
> Installing [Postfix]("https://help.ubuntu.com/lts/serverguide/postfix.html") and [Dovecot]("https://help.ubuntu.com/community/Dovecot") should work with little extra configuration.  Have the web application send mail to username@localhost using your own username.

Thanks for the info but I just found the easiest solution: use an existent SMTP, so I'm using GMail SMTP server, according to the documentation you can send up to 2000 emails daily, much more than what I need for testing. 

The drawback is that I need real e-mail addresses for testing, but that's not a problem

---

