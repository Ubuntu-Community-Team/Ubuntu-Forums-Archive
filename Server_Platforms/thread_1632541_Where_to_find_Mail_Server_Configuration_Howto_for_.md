---
title: "Where to find Mail Server Configuration Howto for Dummies?"
date: 2010-11-28
forum: Server Platforms
---

### Post by rule-of-three on 2010-11-28
Where to find Mail Server Configuration Howto for Dummies?
[B]
Reguirements:[/B]
Autoreply is supported?
User Accounts and other configs in MySQL database..

---

### Post by bsntech on 2010-11-28
I have made a how-to on how I've setup my servers.  It  uses Exim4 for mail transfer, Dovecot for IMAP and POP3 access, and Horde for webmail access.  Horde uses a database for the user accounts and Dovecot and Exim4 are pointed to look at this database for authentication and transfer of mail to the appropriate mailbox.

[http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/312.html]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/312.html")

---

### Post by James78 on 2010-11-28
This should also help you out.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by rule-of-three on 2010-11-28
How about ClamAV and Spam Assassin like here?:
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

---

### Post by James78 on 2010-11-28
More in depth guide.
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

ClamAV with Postfix
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

### Post by windependence on 2010-11-28
You'd be much happier using Zimbra or Citadel. Configuring a mail server and getting it to work correctly can be a big pain. Those two take the pain away. I'm a Zimbra fa myself.
 
-Tim

---

### Post by rule-of-three on 2010-11-28
> **windependence said:**
> You'd be much happier using Zimbra or Citadel. Configuring a mail server and getting it to work correctly can be a big pain. Those two take the pain away. I'm a Zimbra fa myself.
 
-Tim

I know Zimbra:

[http://www.zimbra.com/products/compare_products.html](http://www.zimbra.com/products/compare_products.html)

How about Open Source Edition and SPAM filtering?

I have now Amvis, ClamAV, SpamAssassin (rasos,ddc,pyzor).. no spam ever..

Zimbra will be good buy i4ware Software are Ubuntu Software Partner so we can get price quotes to make PHP/MySQL-based email server maintaining software project so we need to know much. Or do I say to customer buy Zimbra and fail to get 80k EUR of money from project?
That is needed are only Autoreply maintained in MySQL.. everything else I can do without pain..

---

### Post by HermanAB on 2010-11-28
There is nothing easier than running the Easy Install script of Citadel.

---

### Post by rule-of-three on 2010-11-28
> **HermanAB said:**
> There is nothing easier than running the Easy Install script of Citadel.

Give the link then... :)

---

### Post by windependence on 2010-11-28
Just FYI, Zimbra DOES have Spamassin in the open source edition and you don't have to BUY it. Everything in one package, ClamAV, Spamassasin, postfix, etc bundled up nicely and very very stable, but if you want the headache of putting it together yourself, go fot it.
 
-Tim

---

### Post by rule-of-three on 2010-11-28
> **windependence said:**
> Just FYI, Zimbra DOES have Spamassin in the open source edition and you don't have to BUY it. Everything in one package, ClamAV, Spamassasin, postfix, etc bundled up nicely and very very stable, but if you want the headache of putting it together yourself, go fot it.
 
-Tim

Hi,

I will got my,
**Dell PowerEdge R200 with:**

[LIST]
[*]Intel® Xeon® Processor X3220 (8M Cache, 2.40 GHz, 1066 MHz FSB)
[*]2x500Gb SATA2 HDD (Raid 1)
[*]4Gb DDR3 RAM
[/LIST]
At next week.. so I am going to chose Zimbra then.. :D

On my server haves already Polarion ALM and Atlassian FishEye and Confluence so I hope Zimbra is not too much..

I am got only one price quote from making email server web maintenance system and that client was not enough rich to pay me enough.. so I forget that business and focus to beter project for Ubuntu..

---

### Post by rule-of-three on 2010-11-30
Zimbra caused only a problems. I have no use for Apache etc. solutions bundled.. because in my server must have pure apache installation etc.

---

