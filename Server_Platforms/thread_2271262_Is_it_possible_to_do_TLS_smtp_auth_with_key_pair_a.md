---
title: "Is it possible to do TLS smtp auth with key pair and no passwd similar to ssh login?"
date: 2015-03-28
forum: Server Platforms
---

### Post by rkleemann on 2015-03-28
Sorry I incorrectly posted to the chat forum, I hope this is the correct forum...

I'm trying to setup smtp auth with TLS (postfix smtp).

In the same way that ssh login can be performed strictly via key pairs without password login, I was hoping to do the same with smtp auth so that I get the additional security. I've had some trouble with smtp auth hacking and spammers getting relay access.

I know that postfix can be configured to require a certificate, but does that mean that it supports something similar to ssh? Would an email client support a key file, just like putty does for ssh and then used to gain relay access?

thanks
Ricardo

---

### Post by SeijiSensei on 2015-03-29
A quick scan of the [RFC for SMTP with TLS]("https://www.ietf.org/rfc/rfc2487.txt") suggests the answer is no, but my eyes tend to glaze over whenever I read about cryptographic transactions.

You might be able to require the clients to have certificates and only accept ones you know.

---

### Post by rkleemann on 2015-03-29
Thank you for your reply

This is exactly what I'd like to do, accepting only specific client certificates so I don't have to worry about SMTP auth login hacks

Anyone know of this will work?

Regards
Ricardo

---

### Post by SeijiSensei on 2015-03-30
If you haven't already, I'd start by reading this: [http://www.postfix.org/TLS_README.html](http://www.postfix.org/TLS_README.html)

---

