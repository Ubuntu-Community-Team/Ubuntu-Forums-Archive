---
title: "ubuntu to replace windows 2003 server?"
date: 2006-09-07
forum: Server Platforms
---

### Post by geuis on 2006-09-07
Can ubuntu take the place of a windows 2003 server on a network of windows XP pro computers? Handle login, user management, etc?

---

### Post by Glut on 2006-09-08
It can provide basic services, such as login and basic user management. It's not a 2003 spec domain controller and can't be used as one. So, it depends on what you want.

---

### Post by bluefrog on 2006-09-08
as said previously, depends on what you need.

installing/configuring samba-ldap on ubuntu will nevertheless gives you pretty much what any windows server offers you.

PDC, user authentication, file sharing, roaming profile (if needed)...
adding postfix or sendmail will save you the money for an exchange server. Groupware such as egroupware will replace the need for exchange/outlook (not syaing it will do the same, just saying by changing slightly the way work you will find ways to work in collaboration.

James

---

### Post by forgeuk on 2007-01-26
I've sort of got a similar question.

Currently we have a W2003 server, and the domain controller crashes about 20 times a day this week, the boss is frantically trying to fix it.

So is there any way to replace it with Ubuntu + a 3rd party add on?
Does Ubuntu server replace Exchange? so we can all carry on using Outlook on XP pro machines (until I can convince him to have ubuntu clients :D )

I'd really like to suggest to him a Linux-based solution, as he's constantly battling against Microsoft's appauling server software.

I think all we really need is a Domain controller, Exchange server equivelant, FTP, DNS, DHCP etc.

I've been using Ubuntu on my home PC for several months now, and still find it hard to get used to the built-in feature where it doesn't lock up or crash every day :-)

---

### Post by MrHorus on 2007-01-26
> **forgeuk said:**
> 
Does Ubuntu server replace Exchange? 

No - Exchange uses MAPI, similar to IMAP but quite different.

You can have server side email using IMAP but you won't get the groupware functionality like calenders and whatnot by not using Exchange so it depends on the size of your orginisation and what your individual requirements are.

---

### Post by GrammatonCleric on 2007-01-26
Actually there is an Open Source version of Exchange...called OpenGroupWare...

[http://opengroupware.org/en/install/debian/index.html](http://opengroupware.org/en/install/debian/index.html)

...which you can install on Ubuntu.

-GC

---

### Post by GrammatonCleric on 2007-01-27
There is also Scalix Community version...

[http://www.scalix.com/community/](http://www.scalix.com/community/)

...which looks much nicer than OpenGroupWare and does not require a none free plugin for Outlook.

-GC

---

### Post by studiesrule on 2007-01-27
I think there's a seperate fork for servers: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)
I don't know how different it is from the stajndard, but you should check it out

---

### Post by rickyjones on 2007-01-28
> **forgeuk said:**
> I've sort of got a similar question.

Currently we have a W2003 server, and the domain controller crashes about 20 times a day this week, the boss is frantically trying to fix it.

So is there any way to replace it with Ubuntu + a 3rd party add on?
Does Ubuntu server replace Exchange? so we can all carry on using Outlook on XP pro machines (until I can convince him to have ubuntu clients :D )

I'd really like to suggest to him a Linux-based solution, as he's constantly battling against Microsoft's appauling server software.

I think all we really need is a Domain controller, Exchange server equivelant, FTP, DNS, DHCP etc.

I've been using Ubuntu on my home PC for several months now, and still find it hard to get used to the built-in feature where it doesn't lock up or crash every day :-)

If your Windows 2003 server is crashing 20 times a day then you have a serious problem - either hardware or administration failures. I've managed Server 2003 at various clients since it's release - it is rock stable if thrown on good hardware and is setup sensibly.

I don't believe that you'll be able to achieve seamless Server 2003 functionality with Ubuntu. Look at what you /need/ to do and what you /want/ to do.

Just my 2 cents.

-Richard

---

