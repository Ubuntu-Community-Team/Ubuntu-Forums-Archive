---
title: "Setting Up These Servers"
date: 2007-11-22
forum: Server Platforms
---

### Post by PleaseHelp on 2007-11-22
Freeradius
Postfix / MX Server
Authorative DNS
Resolving DNS
DSPAM Or Spam Assassin (Have been looking at DSpam recently as it provides more functionality)
Webmin for the Mail + DNS

HI Im really new to ubuntu and was just wondering if anyone could point me in the right direction on setting up these servers 

Im going to be using them all on one machine.

Any help is welcome 
Thanks Guys n Girls

---

### Post by HermanAB on 2007-11-22
Here is BIND: [http://www.isc.org/index.pl?/sw/bind/index.php](http://www.isc.org/index.pl?/sw/bind/index.php)

and here is Citadel: [http://www.citadel.org](http://www.citadel.org)

That is all you need.  Get BIND working first and ensure that the mail server hostname resolves before you install Citadel.

Cheers,

Herman

---

### Post by PleaseHelp on 2007-11-22
OK Im fairly new to it all so il get bk to u with the results

---

### Post by sciurus on 2007-11-22
Either install a system that will set it all up for you like [Ebox]("http://ebox-platform.com/") or buy a book that will tell you how to do it all yourself like [LPI Linux Certification in a Nutshell, Second Edition]("http://www.oreilly.com/catalog/lpicertnut2/toc.html").

---

### Post by WIGGMPk on 2007-11-23
GLuck to you my freind..


Please post your results, because im ready to kick my server thru the drywall of my apartment.

I think there's all but 10 people in the world that acctually trully understand DNS... And guess what...




THEIR DEAD!!!

For some reason DNS its a big secret LMAO

---

### Post by mellowd on 2007-11-23
DNS isn't that hard

---

### Post by WIGGMPk on 2007-11-23
> **mellowd said:**
> DNS isn't that hard

Yes/No...

Depending on what your doing it can be a pain in the reer. I dont have the time, nor do I have the passion to dig into DNS. It gives me pain behind my eyeballs, and I hate it.

---

### Post by mellowd on 2007-11-24
> **WGGMk said:**
> Yes/No...

Depending on what your doing it can be a pain in the reer. I dont have the time, nor do I have the passion to dig into DNS. It gives me pain behind my eyeballs, and I hate it.

True, it can get fairly complex. The biggest difficulty is the setup. Once that's done though you generally don't need to touch it except for a few updates here and there

---

