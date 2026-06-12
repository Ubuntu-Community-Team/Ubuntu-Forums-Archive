---
title: "What is the username / password when using postfix and  dovecot?"
date: 2007-03-28
forum: Server Platforms
---

### Post by mickbuntu on 2007-03-28
Hello,

Quick questions it is past midnight so forgive my lack of details.

I have looked at:  [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html) 

configuring an email server on ubuntu. 

My question is:

What  will my username and password  be  say for thunderbird?  Does it use my local  login accounts for that?  (the ones that are used for gdm and kdm) ?

Thanks

---

### Post by shufla on 2007-04-24
Hello,

Yes - excatly. Your local username/password pair from /etc/passwd and /etc/shadow files will be used for most system based servers - including postfix and dovecot.

Bye,
Shufla

---

