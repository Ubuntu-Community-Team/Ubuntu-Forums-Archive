---
title: "email server help"
date: 2011-12-10
forum: Server Platforms
---

### Post by TFroehlich3 on 2011-12-10
Alright everyone,
    I have an HP Workstation that used to be a website server for my business. I no longer have the business and want to make it into an email server. I downloaded Ubuntu Server 10.04 LTS to install on it. Can anyone put together a walk through guide that is up to date on the whole process? Or know of any good tutorials? I will post the link for the one that I have been reading, could someone let me know if it would work alright, or if it is to out dated? Thanks! Also I want some input out the hardware... What should I be using for the processor, ram, and HDD space? I was thinking about upgrading the HDD's from a 1TB (1,000GB) drive to a 4 hard drive RAID setup with 500gb of space on each.

Here is the link: [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

---

### Post by yeats on 2011-12-11
These may help:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by TFroehlich3 on 2011-12-15
Thank you so much! Big help!:KS
 
> **yeats said:**
> These may help:
 
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
 
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by Dry Lips on 2011-12-15
Here is an excellent tutorial that covers everything you need to know in order
to set up a secure, spam free email server. 

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

(Covers Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail/Roundcube + Postgrey )

---

### Post by HermanAB on 2011-12-16
Hmm, you can do it the Lego way with Postfix and all the rest, or you can just install Citadel.  The Easy Install script takes about 20 minutes and it can handle tens of thousands of users and 256 terabytes of mail, which should be enough...

---

