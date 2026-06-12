---
title: "Which CalDAV/CardDAV/WebDAV server, encrypted, without root access?"
date: 2014-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Cubytus on 2014-05-06
Hi community, 

this question is about a Linux shared hosting I rent, and as shared, doesn't provide any root access. For this reason and because it never worked properly, I ditched ownCloud, which seems too immature yet to be usable.

Now, this server already has a built-in WebDAV server, but it's mostly useless, and badly supported on all systems I tested it upon. Currently is has no CalDAV nor CardDAV, and I would like to have these functions under my control. True self-hosting would be possible for CalDAV and CardDAV, but less than ideal as a home server is not immune to downtimes and crashes, and is not managed 24/7 the way a professional server is.

Of course I first read Wikipedia's [page]("http://en.wikipedia.org/wiki/Comparison_of_CalDAV_and_CardDAV_implementations#Server_implementations") on these servers, but they don't mention if the database could hold entirely encrypted informations. So, should the server be compromised in any way, retrieved data would be useless.

What server software would allow such a setting?

---

### Post by SeijiSensei on 2014-05-06
How much do you pay for shared hosting?  You can rent a virtual Linux server on which you can have root access for as little as [$5/month]("http://www.1and1.com/vps-hosting?gclid=CP3IooDEmL4CFe07OgodPhoAnw&ac=OM.US.US430K49953T7073a&ovm_kp=SERVER-GE-BM-DK-SN&ovm_wm=BM-Vps+Virtual+Linux&ovm_kw=_+machine%20+linux%20+virtual&ovm_sc=none&s_kwcid=AL!3115!3!40699681018!b!!g!!+machine%20+linux%20+virtual&ef_id=U2l68gAAAGEeDBi@:20140507001442:s").  I use [Linode]("http://www.linode.com/").  More expensive, but worth it in my experience if you're hosting services for others professionally as I do.

---

### Post by Cubytus on 2014-05-07
Hm, I think that's $100 a year. The goal was, and still is to stay as far away as possible from police states. That means, nothing in the US nor France nor Germany. I though about a VPS, but eventually decided against it not because of cost consideration (although being Switzerland-based, cost is up to par with Swiss' average income), but required management. I don't have the time to check daily or weekly if there are updates available, to apply them, or making sure the network works as expected "With great power come great responsabilities".

 I only care about applications. From Wikipedia's pages, there's SabreDAV (incidentally used by ownCloud), Baïkal and DAViCal, but nothing is said about encrypting the database.

---

