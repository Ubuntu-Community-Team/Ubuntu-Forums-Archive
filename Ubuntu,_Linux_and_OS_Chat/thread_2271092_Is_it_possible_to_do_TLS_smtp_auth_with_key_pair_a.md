---
title: "Is it possible to do TLS smtp auth with key pair and no passwd similar to ssh login?"
date: 2015-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by rkleemann on 2015-03-27
Hi,

I'm trying to setup smtp auth with TLS (postfix smtp). 

In the same way that ssh login can be performed strictly via key pairs without password login, I was hoping to do the same with smtp auth so that I get the additional security. I've had some trouble with smtp auth hacking and spammers getting relay access.

I know that postfix can be configured to require a certificate, but does that mean that it supports something similar to ssh? Would an email client support a key file, just like putty does for ssh and then used to gain relay access?

thanks
Ricardo

---

