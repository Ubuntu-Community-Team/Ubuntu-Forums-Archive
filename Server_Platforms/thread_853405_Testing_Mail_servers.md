---
title: "Testing Mail servers"
date: 2008-07-08
forum: Server Platforms
---

### Post by Teso on 2008-07-08
Hi

I'm a WIndows User and want to install one of these 3 mail servers but don't know wich is the best. 

It's important to me

1) Ease of installation and administration
2) Ease of migration (From Mdaemon - Windows)
3) Security (hack proof and antispam)
4) Speed 

This mail servers have what I need but I do not used them before

[LIST]
[*]Courier
[*]Postfix
[*]Citadel
[/LIST]

I'll try first in ubuntu desktop, then in server.
I'll use Webmin

Thanks!!

Recomendations and tips appreciated!

---

### Post by juan@forum on 2008-07-08
first: you need to understand what the software you mention does, they are all different.
second: you need to understand which services you wish to implement in your mail server

---

### Post by cdenley on 2008-07-08
I like zimbra.
[https://sourceforge.net/project/showfiles.php?group_id=224243](https://sourceforge.net/project/showfiles.php?group_id=224243)

---

### Post by John.Klockenkemper on 2008-07-08
Zimbra is an application that the company I work for supports.

Its excellent, fairly quick, and easy to deploy.

---

### Post by windependence on 2008-07-09
I'll put in a third word for Zimbra. Be aware though, it like it's own box. You would not want to run much else on the Zimbra box. Excellent product though.

-Tim

---

### Post by jmirick on 2008-07-09
I have had a Postfix server running for about a year, O'Reilly has a good book on it and in general it has been very good.  We have lots of other stuff on a Dell 2600 that it's on, it's not a resource hog.

---

### Post by artcancro on 2008-07-18
> **cdenley said:**
> I like zimbra.

I don't.  They open source a stripped-down version but if you want it to do anything useful you have to buy the expen$ive proprietary version.


Definitely go with Citadel instead.   [http://www.citadel.org](http://www.citadel.org)

True open source (GPL).

---

### Post by cdenley on 2008-07-18
> **artcancro said:**
> I don't.  They open source a stripped-down version but if you want it to do anything useful you have to buy the expen$ive proprietary version.


Definitely go with Citadel instead.   [http://www.citadel.org](http://www.citadel.org)

True open source (GPL).

Open-source version can do everything I need it to. I haven't found anything citadel can do that zimbra open-source can't. It's web interface is much better. Citadel doesn't work well with an LDAP server. Zimbra includes an ldap server and integrates with POSIX accounts and samba very well. The only reason I would purchase another version of zimbra would be for guaranteed support. I had nothing but problems with citadel. Zimbra seems rock solid.

---

### Post by songshu on 2008-07-19
Zimbra seems to be behaving fine in my testing environment although i did not put it up to the test. 
(Note: you need the licensed version if you want to do clustering or use outlook, blackberry connectors to make it a full exchange replacement, but the open source functionality seems pretty complete without those)

if it is what you need the added complexity (just like citadel etc..) might be worth it.

personally i will stick with my simple but solid combination of postfix+dovecot for now .

---

### Post by windependence on 2008-07-20
Might be more complex internally but sure is less painful to install than cooking up your own. 

The "features" artcancro say are missing can almost all be replaced with another open source app that interfaces with Zimbra. It ceratinly isn't crippled in any way. I have several installations running just fine at local businesses and one sever that runs 5 businesses at once with no problems. It's a complete solution in one package. 

IMHO, citadel's interface is a bit funky (although I like the product). Some people find it rather weird so in those cases I use something else. the two (citadel and Zimbra) are really different products and do very different things.

-Tim

---

