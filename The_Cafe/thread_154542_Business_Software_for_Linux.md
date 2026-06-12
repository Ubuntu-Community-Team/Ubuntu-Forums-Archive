---
title: "Business Software for Linux"
date: 2006-04-03
forum: The Cafe
---

### Post by klingy on 2006-04-03
Hi everyone. 

The reason for this post is two-fold - the first being my company has now switched almost entirely to Ubuntu. And we need to accomodate for the software we used in Windows. 

Second, I am starting a blog on businesses using linux, and would like some information for the introductory post. 

I'm looking for suggestions for the following types of software if possible: 

. Contact Management (Not only keeping contact details for clients, but also recording communications)
. Accounting (Doesn't have to be "submittable" to our accountant as I'm doubtful there is any *nix software that accountants will take ;) 


Evolution covers our e-mail needs perfectly, but these two areas seem to have not been filled as of yet. 

Many thanks in advance for any advice, tips or links to software (please keep them FOSS!),

klingy

---

### Post by stuporglue on 2006-04-03
For accounting, you should look at GnuCash

[http://www.gnucash.org/](http://www.gnucash.org/)

It users a double entry ledger system and can handle debt, loans credit and lots of other stuff. It's somewhat ugly since the stable version uses Gtk1, but it works fine. 

A little bit of a learning curve to get it set up, but once it's up, using it is nice and easy.

---

### Post by klingy on 2006-04-03
Many thanks stuporglue!

I shall look right into it :D

---

### Post by maruchan on 2006-04-03
Hi Klingy,

The blog idea sounds like it could be a valuable resource. I hope some of these links help:

Accounting-related software:
[http://linuxlinks.com/Software/Financial/Accounting/](http://linuxlinks.com/Software/Financial/Accounting/)
[http://www.compiere.org/](http://www.compiere.org/)
[http://proj.chbs.dk/accounting/](http://proj.chbs.dk/accounting/)
[http://linuxlinks.com/Java/Financial/](http://linuxlinks.com/Java/Financial/)

I'm not sure what you mean by contacts, but here's my best shot:
[http://linuxlinks.com/Java/Productivity_Tools/PIM/](http://linuxlinks.com/Java/Productivity_Tools/PIM/)
[http://linuxlinks.com/Software/ProductivityTools/Address_Books/](http://linuxlinks.com/Software/ProductivityTools/Address_Books/)
[http://linuxlinks.com/Software/ProductivityTools/PIMs/](http://linuxlinks.com/Software/ProductivityTools/PIMs/)

---

### Post by klingy on 2006-04-03
[QUOTE=maruchan]Hi Klingy,

The blog idea sounds like it could be a valuable resource. I hope some of these links help:

Accounting-related software:
[http://linuxlinks.com/Software/Financial/Accounting/](http://linuxlinks.com/Software/Financial/Accounting/)
[http://www.compiere.org/](http://www.compiere.org/)
[http://proj.chbs.dk/accounting/](http://proj.chbs.dk/accounting/)
[http://linuxlinks.com/Java/Financial/](http://linuxlinks.com/Java/Financial/)

I'm not sure what you mean by contacts, but here's my best shot:
[http://linuxlinks.com/Java/Productivity_Tools/PIM/](http://linuxlinks.com/Java/Productivity_Tools/PIM/)
[http://linuxlinks.com/Software/ProductivityTools/Address_Books/](http://linuxlinks.com/Software/ProductivityTools/Address_Books/)
[http://linuxlinks.com/Software/ProductivityTools/PIMs/](http://linuxlinks.com/Software/ProductivityTools/PIMs/)[/QUOTE]

Wow! Lot's of "link material", many thanks for that. I shall look into them. Have you used any personally?

---

### Post by helpme on 2006-04-03
Some other software you could take a look at:
[http://www.linuxcanada.com/quasar.shtml](http://www.linuxcanada.com/quasar.shtml)
[http://www.appgen.com/](http://www.appgen.com/)
[http://www.sql-ledger.org/](http://www.sql-ledger.org/)
[http://www.osas.com/html/7ZE16RR4S4.htm](http://www.osas.com/html/7ZE16RR4S4.htm)
[http://www.kumula.org/](http://www.kumula.org/)

Edit:
Seems maruchan was faster than me. :D

---

### Post by maruchan on 2006-04-03
> Have you used any personally?

Heck no! My job as a Linux zealot is not to actually use the software, but to push as many sub-standard "options" on people as possible.

*tongue in cheek* ;)

(Actually I'm a graphics guy, so accounting software is something I rush out to buy on April 14th...)

---

### Post by klingy on 2006-04-03
[QUOTE=maruchan]Heck no! My job as a Linux zealot is not to actually use the software, but to push as many sub-standard "options" on people as possible.

*tongue in cheek* ;)

(Actually I'm a graphics guy, so accounting software is something I rush out to buy on April 14th...)[/QUOTE]

Hehe! We are actually a graphics company too 8) (Well, we term it "Corporate Identity Design", just for kicks :D )

My blog is up! Is it OK to post the link here?

---

### Post by maruchan on 2006-04-03
Sure, fire away, no problem with posting links here.

---

### Post by superchar42 on 2006-04-03
Is there any sort of software that allows for inventory management? I do home party sales, and would prefer a program that does that, maybe has the capabilities to store contacts and contact info as well.. but that's wishful thinking. There's one on the windows/mac market: [http://www.mlmeasymoney.com](http://www.mlmeasymoney.com) -- they made a company specific one for Pure Romance, the company that I'm with. Cool software, but I talked to the guy and he's got no intentions of branching out to a linux audience.

---

### Post by paul cooke on 2006-04-03
> **klingy]Hi everyone. 

The reason for this post is two-fold - the first being my company has now switched almost entirely to Ubuntu. And we need to accomodate for the software we used in Windows. 

Second, I am starting a blog on businesses using linux, and would like some information for the introductory post. 

I'm looking for suggestions for the following types of software if possible: 

. Contact Management (Not only keeping contact details for clients, but also recording communications)
. Accounting (Doesn't have to be "submittable" to our accountant as I'm doubtful there is any *nix software that accountants will take  said:**
> 

CRM (Customer Relationship management) software...
AKA Contact management for the salesforce

code for download
[http://sourceforge.net/projects/compiere/](http://sourceforge.net/projects/compiere/)

their website:
[http://www.compiere.org/](http://www.compiere.org/)


apparently it's a server based program that is interfaced with using a browser

makes life easier for the client side.

this is stuff that scales right up to Global salesforces

oh... it requires Oracle on the server side... expensive... (£9000 approx for Standard Edition (per processor licensed) or £174 per named user licensed (and you have to get a minimum of 5 per user licenses as well)) as well as SUN Java

don't you just hate it when some FOSS solution is tied to a proprietary product...

ps, my head exploded just trying to work my way round the Byzantine per processor/per user licensing pricing system for Oracle 10g :confused:  GPL makes things so much simpler... :)

[QUOTE]Oracle Database Standard Edition  	 5 Named Users Plus*

* Oracle Database Standard Edition can only be licensed on servers that have a maximum capacity of 4 single core processors cores. For multicore chips, the maximum number of cores per server is determined by multiplying the core processor licensing factors (as contained in the processor definition) by the number of cores. The result must be less than or equal to 4 and the total number of cores must be less than or equal to 8. If licensing by Named User Plus, the minimum is 5 Named User Plus licenses.Additionally, it may be licensed on a single cluster of servers supporting up to a maximum of four single-core processors cores per cluster (2 2-way nodes, 4 1-way nodes, and 1 1-way and 1 3-way). For multicore chips, the maximum number of cores per cluster is determined by multiplying the core processor licensing factors (as contained in the processor definition) by the number of cores. The result must be less than or equal to 4 and the total number of cores in the cluster must be less than or equal to 8. 

ps, forgot this link:

[http://linas.org/linux/pm.html](http://linas.org/linux/pm.html)

should find some leads there... :)

---

