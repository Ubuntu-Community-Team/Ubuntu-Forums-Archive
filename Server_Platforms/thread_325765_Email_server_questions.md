---
title: "Email server questions"
date: 2006-12-26
forum: Server Platforms
---

### Post by 1oki on 2006-12-26
Hello all, got a question for you. In the near future I will be responsible for setting up an email server for my practice with outlook 2003, outlook express, imap, pop3, functionality. I was wondering which would be easier to setup, MS exchange or Ubuntu server... I'm sure MS exchange would be easier, but lets face it... its M$ and I don't want to go down that path. Any help or info on the matter would be great. I did find this guide:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

if I follow that should it work with what i want it to do? 
I guess I just need to hear someone who tried it and worked without any problems. I'm not an expert in Linux, but I am also by far not stupid in Linux and can figure things out. So if you want to take that approach that would be grand! thanks all in advance! ;)

---

### Post by evilghost on 2006-12-26
I just got done completing my mailserver.  I'm running Dovecot + Postfix, I compiled both from source so I could ensure that SSL and the dovecot SASL authentication mechanism was working.

I'd follow the documentation for dovecot ([http://www.dovecot.org](http://www.dovecot.org)) and postfix ([http://www.postfix.org)](http://www.postfix.org)).

I'll certainly be willing to help you out with any questions you have.

---

### Post by 1oki on 2006-12-26
> **evilghost said:**
> I just got done completing my mailserver.  I'm running Dovecot + Postfix, I compiled both from source so I could ensure that SSL and the dovecot SASL authentication mechanism was working.

I'd follow the documentation for dovecot ([http://www.dovecot.org](http://www.dovecot.org)) and postfix ([http://www.postfix.org)](http://www.postfix.org)).

I'll certainly be willing to help you out with any questions you have.

Awesome! I will look into it. But I don't know how long it will be until I start this project. Just doing a little research right now... Waiting for the ok to order a nice duel xeon server ;)

---

### Post by evilghost on 2006-12-26
Sounds good.  Both Dovecot and Postfix are well documented and support a heavy load.  I favor Dovecot over Courier and UW-IMAP by far, mostly due to performance and security.  I favor postfix over qmail because postfix tends to be a more "modern" MTA and is a little easier to configure/manage.

---

### Post by MrHorus on 2006-12-27
> **1oki said:**
> 
I guess I just need to hear someone who tried it and worked without any problems. 


That would be me then :)

I run a combination of exim4, procmail and courier-imap and that trilogy should be idea for your purposes.

I had a small amount of problems trying to get encrypted connections to work with TLS but since your (presumably) accessing it over a controlled LAN then I don't see this being a huge problem although do bear in mind that sending plaintext passwords is never a good thing.

---

### Post by MJN on 2006-12-29
> **evilghost said:**
> I just got done completing my mailserver. I'm running Dovecot + Postfix, I compiled both from source so I could ensure that SSL and the dovecot SASL authentication mechanism was working.
 
No need for manual building - the repository packages of both Postfix and Dovecot support encrypted authentication.
 
Mathew

---

### Post by evilghost on 2006-12-29
> **MJN said:**
> No need for manual building - the repository packages of both Postfix and Dovecot support encrypted authentication.
 
Mathew

True, but I'm running Dovecot 1.0rc15, not available in the repos, it was still pre 1.0 when I looked.  Additionally postfix isn't compiled with the support for dovecot's SASL mechanism as documented in [http://www.postfix.org/SASL_README.html#build_dovecot](http://www.postfix.org/SASL_README.html#build_dovecot)

I'm actually using Dovecot's SASL with postfix, [http://wiki.dovecot.org/PostfixAndDovecotSASL](http://wiki.dovecot.org/PostfixAndDovecotSASL)

---

### Post by Brazen on 2006-12-29
Email is one of the things I am not admining on linux.  Unless you want all the features of Exchange, though, I imagine it would be MUCH harder to setup for just basic IMAP and POP3 email functionality.

For one thing, Exchange requires a Windows domain, so you have to set that up first.  Even after the domain is setup and working smoothly, Exchange is no simple beast.  And if you are not using all Outlook (full version, not Express, I think) clients, then it is additional steps to setup POP3, SMTP, and IMAP access.

---

