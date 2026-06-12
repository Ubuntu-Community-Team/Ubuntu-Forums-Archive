---
title: "[SOLVED] recommend exchange server for linux"
date: 2008-10-30
forum: Server Platforms
---

### Post by mitchroberts on 2008-10-30
can anyone recommend any software that is like microsoft exchange server but linux?I guess what i'm looking for is linux exchange server.

---

### Post by adaptr on 2008-10-30
There is no free solution that will do what Exchange does; however, look at **Zimbra **for a close match.

---

### Post by alienprdkt on 2008-10-30
**Ubuntu + Postfix + Courier IMAP + MySQL          + Amavisd-new + SpamAssassin + ClamAV          + SASL + TLS + SquirrelMail + Postgrey  **
[http://flurdy.com/docs/postfix/index.html#top](http://flurdy.com/docs/postfix/index.html#top)


[http://www.postfix.org/](http://www.postfix.org/)

---

### Post by adaptr on 2008-10-30
That doesn't even come close to offering Exchange's functionality.. it's merely a very complete Postfix setup, but nothing even resembling groupware is in that list.

---

### Post by alienprdkt on 2008-10-30
> **adaptr said:**
> That doesn't even come close to offering Exchange's functionality.. it's merely a very complete Postfix setup, but nothing even resembling groupware is in that list.
Well excuse me' when I used exchange it was to host email.... and that is what I do now with post fix ;)

---

### Post by lykwydchykyn on 2008-10-30
Are you looking for a drop-in replacement for clients running outlook, or just some kind of groupware/email/calendaring solution?

---

### Post by mitchroberts on 2008-10-30
> **lykwydchykyn said:**
> Are you looking for a drop-in replacement for clients running outlook, or just some kind of groupware/email/calendaring solution?

here is what i have so i can do it both ways i am running ubuntu with terminal service installed and the client pc's also have outlook i was thinking of a replacement for clients running outlook but when they log in to terminal server they could just as easy check there email there.What would be the best way i would think just using outlook but i am new to linux so any help would be appreciated.

---

### Post by cdenley on 2008-10-30
I just installed zimbra network pro today. It isn't free, but it comes with an outlook connector which I think provides the same functionality as exchange from inside outlook. I've never used exchange, though, so I can't be sure.

---

### Post by lykwydchykyn on 2008-10-30
> **mitchroberts said:**
> here is what i have so i can do it both ways i am running ubuntu with terminal service installed and the client pc's also have outlook i was thinking of a replacement for clients running outlook but when they log in to terminal server they could just as easy check there email there.What would be the best way i would think just using outlook but i am new to linux so any help would be appreciated.

I guess what I'm driving at is whether you want a 100% feature-for-feature clone of exchange, or if you just need generic groupware.  If I'm not mistaken Outlook can connect to pop3 and IMAP.

If you're looking to implement an alternative to exchange, I think you need to start by asking yourself which features are important and looking at software that implements those features.

---

### Post by mitchroberts on 2008-10-30
> **lykwydchykyn said:**
> I guess what I'm driving at is whether you want a 100% feature-for-feature clone of exchange, or if you just need generic groupware.  If I'm not mistaken Outlook can connect to pop3 and IMAP.

If you're looking to implement an alternative to exchange, I think you need to start by asking yourself which features are important and looking at software that implements those features.

it does not have to be a clone just alternative will do i think a 100% feature-for-feature clone would be nice but a alternative will do. 
i need it mostly for calender and to get the out of office assistant to work.The people i am doing this for like that for some reason?:confused:

---

### Post by perspectoff on 2008-11-18
Kolab.

No question.

It is the only groupware server that is fully open-source, powerful, scalable, and Outlook compliant (with a connector).

Zimbra does not use the GPL license -- it is "pseudo-open source." The community edition is crippled -- does not have easy backup/restore functions, and requires licensing for Outlook connectivity.

Zimbra works nicely (it has an AJAX interface) but is owned by Yahoo (or whoever buys Yahoo). Do you want to trust that situation?

Scalix is a similar situation. it works nicely, but is proproetary and requires licensing for full function.

Zafara is a superb groupware solution based in Holland, and it has a community version, but like the other two, requires licensing for full functionality.

Kolab is the only truly open source server with similar features and functionality. With its integrated Horde, web access is seamless. 

Other alternatives include eGroupware, which also has connectors to popular clients, such as Mozilla and Kontact (in KDE). This is probably my second choice solution. I don't like its native interface, and it doesn't seem as scalable as Kolab, but it certainly is easy to install and configure.

OpenGroupware is another solution I haven't tried, but it apparently also has a large community, and has a simplified installer. eGroupware and OpenGroupware both have had a long development history and rivalry.

Citadel is an interesting open source solution (which is Kolab compatible) and I'm not quite sure why this hasn't caught on at universities instead of Zimbra. It's a clever groupware solution that is reminiscent of bulletin boards, and is user friendly and sensible, given this history. Perhaps it has the perception of being a hobbyist's groupware solution.

Bottom line for a small to mid-size business? Kolab.

---

### Post by CrucifiedEgo on 2008-11-18
> **perspectoff said:**
> 
Kolab ...With its integrated Horde, web access is seamless. 

Not to pull the thread OT(even though that's exactly what i'm doing, i guess,) but Horde and seamless are words that can only exist in the presence of the word "not."  End-users despise it in my experience.

---

### Post by mike010 on 2008-11-18
> **perspectoff said:**
> Kolab.

No question.

It is the only groupware server that is fully open-source, powerful, scalable, and Outlook compliant (with a connector).

Zimbra does not use the GPL license -- it is "pseudo-open source." The community edition is crippled -- does not have easy backup/restore functions, and requires licensing for Outlook connectivity.

Zimbra works nicely (it has an AJAX interface) but is owned by Yahoo (or whoever buys Yahoo). Do you want to trust that situation?


Scalix is a similar situation. it works nicely, but is proproetary and requires licensing for full function.

Zafara is a superb groupware solution based in Holland, and it has a community version, but like the other two, requires licensing for full functionality.

Kolab is the only truly open source server with similar features and functionality. With its integrated Horde, web access is seamless. 

Other alternatives include eGroupware, which also has connectors to popular clients, such as Mozilla and Kontact (in KDE). This is probably my second choice solution. I don't like its native interface, and it doesn't seem as scalable as Kolab, but it certainly is easy to install and configure.

OpenGroupware is another solution I haven't tried, but it apparently also has a large community, and has a simplified installer. eGroupware and OpenGroupware both have had a long development history and rivalry.

Citadel is an interesting open source solution (which is Kolab compatible) and I'm not quite sure why this hasn't caught on at universities instead of Zimbra. It's a clever groupware solution that is reminiscent of bulletin boards, and is user friendly and sensible, given this history. Perhaps it has the perception of being a hobbyist's groupware solution.

Bottom line for a small to mid-size business? Kolab.


i am also looking for something like this Kolab looks nice.Thanks one more thing i did see a kde client and a windows client i will not need it but what about gnome?all of the users are running windows so i will just install kolab windows email client.I am going to look at all the other software you have listed but this one seems to be what i am looking

---

### Post by birkopf on 2008-12-04
> **mike010 said:**
> i am also looking for something like this Kolab looks nice...

I just started having issues with my free exchange server and I am looking for something better. 

I have HTC with WindowsMobile6 and Kubuntu 8.04 64bit. 

Just two questions:

1) Is there (at the moment) free linux exchange server that no-one mention in this topic yet? I found Zafara, Bynari InsightServer, PostPath, UNISON, and few more but none of them is free

2) If not - Will it be possible to create one ?

---

### Post by batfastad on 2008-12-04
Take a look at Zimbra.
It's under a non-GPL license though, something called the Yahoo Public License. But the terms are still pretty flexible, especially coming from Exchange!

It's a full groupware solution: calendar, email, tasks/notes, IM between users and a sweet AJAX remote interface.

There's an open-source version which does it all, but only for a single domain. Backups can only be done offline as well.

Then a paid-for version (Network Edition) which includes all the licensed and cool proprietory code for Activesync/Outlook sync, Blackberry, Apple isync, multiple domains and online incremental backups. And a few other things.

I'm planning on migrating our Exchange Small Business Server 2003 (15 users) over to Zimbra (Network Pro Edition, with Zimbra Mobile) once v6 is released, April 2009 is the estimated date.
There's some big changes/upgrades/new features coming with v6!

HTH, B

---

### Post by mitchroberts on 2008-12-04
yeah i have went with Zimbra i was able to find a single copy 
off there website.thanks

---

### Post by veloce on 2008-12-04
> **birkopf said:**
> 

1) Is there (at the moment) free linux exchange server that no-one mention in this topic yet? I found Zafara, Bynari InsightServer, PostPath, UNISON, and few more but none of them is free



No one has mentioned OBM obm.org which I came across accidentally recently.  Never used it but great things are claimed on their site.  Apparently it has been in the Ubuntu repos since Hardy.

---

### Post by scorp123 on 2008-12-06
> **veloce said:**
> Apparently it has been in the Ubuntu repos since Hardy. yup. ```
sudo apt-get install obm
``` ... can't get easier than that :D

---

### Post by LarsW_Tierp on 2008-12-07
Take a look at Axigen mailserver.

---

### Post by veloce on 2008-12-07
> **scorp123 said:**
> yup. ```
sudo apt-get install obm
``` ... can't get easier than that :D

And does it perform as well as it claims?

---

### Post by scorp123 on 2008-12-07
> **veloce said:**
> And does it perform as well as it claims? It performed OK in my test environment that I had setup, I did not see any issues whatsoever with it ... but ultimately my boss decided to go with the paid version of Zimbra ... so that's what we are using now.

---

### Post by troyready on 2008-12-07
I just wanted to cast my vote in this to Zarafa (zarafa.com).

It is a feature complete open-source groupware server, and even supports multi-company (i.e. hosted) setups. I also particularly like the 100% open-source Exchange Activesync integration (my phone gets push e-mail, and it's all free).

The only significant piece that you would have to buy is Outlook support, which all of the other significant groupware servers appear to charge for as well.

All in all, I think it can't be beat.

---

