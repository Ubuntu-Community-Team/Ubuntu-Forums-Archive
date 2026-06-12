---
title: "getting CAFF work (from pkg signing-party)"
date: 2009-03-21
forum: Security
---

### Post by bmhm on 2009-03-21
Hi all,

I'd like to use the tool **caff** from the package "signing-party". It sends mail with encrypted signatures to those who you just signed (PGP/GPG).

Is there a good tutorial on how to set up an *MTA*? I just cannot send mails, no one receives them. On openSuSE all I had to do was to change my hostname to a proper value, but this didn't work on Ubuntu. 
As I understand, I need either exim4 or postfix. 

As I have seen, there is no article related to caff on the wiki. Would be glad if someone could write one.

Regards

---

### Post by galfly on 2010-08-10
I'm guessing you might have resolved this problem by now but I'll reply anyway, in case someone else needs help:

caff uses smtp. You need to set up your smtp server first. You can do this for most email providers --you don't need to run your own domain or email server to set up your smtp.

Then you need to configure ~/.caffrc file to configure it correctly. 

It works smoothly. Let me know if you have more questions.

maya--

> **bmhm said:**
> Hi all,

I'd like to use the tool **caff** from the package "signing-party". It sends mail with encrypted signatures to those who you just signed (PGP/GPG).

Is there a good tutorial on how to set up an *MTA*? I just cannot send mails, no one receives them. On openSuSE all I had to do was to change my hostname to a proper value, but this didn't work on Ubuntu. 
As I understand, I need either exim4 or postfix. 

As I have seen, there is no article related to caff on the wiki. Would be glad if someone could write one.

Regards

---

