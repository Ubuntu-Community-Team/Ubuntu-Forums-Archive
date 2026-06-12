---
title: "Accounting Package"
date: 2006-02-15
forum: Server Platforms
---

### Post by alamba on 2006-02-15
Hi,

I'm looking for a OSS accounting package for an SME client. Needs to be web based since he needs to host it in the data center with number of people using from different locations.

Any suggestions? Particularly  looking for one that would be reasonably easy to configure and maintain on a ubuntu server.

Regards,
Akshay

---

### Post by alamba on 2006-02-18
bump

---

### Post by Revolution on 2006-02-18
I can only suggest SQL-Ledger

Not too many Open Source and free packages around.
If the SME is a manufacturer then SQL-Ledger would be a useful package.
Its the next thing I'm planning on setting up for a small manufacturer.

---

### Post by alamba on 2006-02-19
I'm genuinely surprised on the lack of web based OSS account packages out there. Wonder what's the reason for that. 

A

---

### Post by nocturn on 2006-03-01
There are some (I think opengroupware includes this too).

But one of the issues with professional accounting packages is that they have to comply with local laws, which are different in many countries.

---

### Post by trentend on 2006-03-01
SQL-Ledger seems to be a good choice for a dedicated accounting package.  It has a large user base, and is easily customised.  I believed localisation is well supported and relatively simple.  It is being developed towards more general business use, as well.

We have elected to go down the route of Ofbiz, as our immediate needs are more biased towards production management. An accounting module is in heavy development, although I am not sure that this will be open source.  Ofbiz (Opentaps) is definately a professional level package and looks most promising in the Open Source ERP category.

---

### Post by rich on 2006-03-01
I spent quite a long time investigating this sort of thing a few years ago. 

One that may be worth a look is compiere.org although (to be honest) I was never able to work out whether it was going to be an enourmous waste of my time. Also needs oracle. 

The trouble is that accountancy is 
(a) boring
(b) important
(c) dangerous to get wrong

which is why sage et al make a tidy living. 


Rich

---

### Post by trentend on 2006-03-01
I had a look at Compiere myself, and came to the conclusion that unless I paid for support/consultancy it wasn't going to work for me.  Here in the UK localised changes are not fed back into the code base, and one needs to purchase support from a  local consultant to get a working system.

They were even looking to charge for an installation to test.  I walked away at that point, and am much happier with my choice of Ofbiz.  It's going to be huge, I tell you.

---

### Post by alamba on 2006-03-05
Thanks guys for pointing me to sql-ledger. From what I've been able to figure out so far, its a breeze to install with PostgreSQL however mySQL support is rather limited. 

Is it safe/ok to install 2 databases on the same server? My server currently runs mySQL for SugarCRM. Would it be ok to host this on the same machine?

A

---

### Post by rivasdiaz on 2006-03-06
[QUOTE=alamba]Is it safe/ok to install 2 databases on the same server? My server currently runs mySQL for SugarCRM. Would it be ok to host this on the same machine?[/QUOTE]

No problem with that. Just whatch out your CPU ussage and your disk space. Every service you install will take some of those resources.

---

### Post by alamba on 2006-03-06
[QUOTE=rivasdiaz]No problem with that. Just whatch out your CPU ussage and your disk space. Every service you install will take some of those resources.[/QUOTE]

Thanks riva. I'll definately keep an eye out for resource utilization. How about contention issues? Do the 2 databases use any common software resources like connectors, etc? 

A

---

