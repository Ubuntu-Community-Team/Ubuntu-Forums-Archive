---
title: "Cluster old systems - Worthwhile?"
date: 2008-03-10
forum: Server Platforms
---

### Post by quietas on 2008-03-10
Here's my dilemma.

At work I have been replacing all of our aging Win98 machines, thus I have 12 800-1000hmz P3's and Athlons sitting around. The only realistic use for them I could think of was Linux. Even then it would be mostly useless as we have a primarily Windows network with all of our software being Windows dependent.

12x 800mhz, 256mb ram, would they be worthwhile to cluster for a rendering server or just ditch them for 3-5 new systems?

---

### Post by netlogic on 2008-03-10
I think it is totally pointless. How about one 8 core machine? It would pay for the energy saving within one year for running 12x850mhz machine. Also, do you really need that much power on a home Linux machine? You kind of need it for Vista Aero's awful power draining acceleration. If I was you, I would sell them on ebay and buy new ram, cpu, and mother board with that money. Just sell them at $35/piece. $35*12=$420. It should be more than enough to buy a new motherboard, ram, and cpu. If you really need to learn clustering, buy a server motherboard with 32 gigs of ram and run 12 VMs in one machine. You will save around  $50 to $100 per month on your electric bill.

---

### Post by Rick Z on 2008-03-18
Yes, if you have the budget to purchase a new server, I would agree using virtualization.  You will save a lot of electric bills.  

However, those old pc can probably configure as backup server.  I configured one of old pc that runs PIII, 128ram, 500Gig HD (IDE hard drive is pretty cheap now).  I use it only to backup computer images.  The backup server only turns on when I need to redeploy or restore image of a pc.  This backup server will save you “hours” of Windows updates per pc.  I am using Clonezilla, but there’re many others.

For learning proposes, you can use Clustering and setup a backup server.  Of course, many free apps can be deploying using linux.

---

### Post by crouton on 2008-03-21
Consider using them as diskless workstations.  If you have the right network cards, you can use LTSP (google for it) to connect to a central server that offers the usual assortment of desktop apps (web, email, etc)  It can save you quite a chunk of change if the majority of your users are not using specialized Windows applications.  Of course then you have to learn it, support it, etc but that's a valid tradeoff for some people.

---

