---
title: "Fibre or Gigabit Dillemma"
date: 2011-06-08
forum: Server Platforms
---

### Post by spynappels on 2011-06-08
I have a problem and I'm trying to work out the best solution, but I need some help as I am less than knowledgeable on fibre networking.

I have a variety of servers and workstations which need to be able to move very large blocks of data around as quickly as possible. We're talking about up to 4-5GB data in one go, and the transfer speeds need to be as fast as I can get them.

I've been told to look at using fibre links between the servers themselves, and between the servers and workstations.

Can fibre lines be used in exactly the same way as ethernet cables, assuming I have fibre switches of course? Could I assign an IP address to the fibre interface on a server and use that interface exactly the same way as I would an eth0 interface? And would a fibre NIC which is advertised as being for connecting to a SAN do the trick?

Alternatively, would using 2x1GbE interfaces and using link aggregation be a better option, at least to the workstations?

I'm trying to keep the costs down as much as possible, and I am aware that the server storage write speeds will be an other issue to consider, but I am just looking for feasibility of and arguments for and against using fibre for ethernet style connectivity.

---

### Post by blind2314 on 2011-06-08
> **spynappels said:**
> I have a problem and I'm trying to work out the best solution, but I need some help as I am less than knowledgeable on fibre networking.
 
I have a variety of servers and workstations which need to be able to move very large blocks of data around as quickly as possible. We're talking about up to 4-5GB data in one go, and the transfer speeds need to be as fast as I can get them.
 
I've been told to look at using fibre links between the servers themselves, and between the servers and workstations.
 
Can fibre lines be used in exactly the same way as ethernet cables, assuming I have fibre switches of course? Could I assign an IP address to the fibre interface on a server and use that interface exactly the same way as I would an eth0 interface? And would a fibre NIC which is advertised as being for connecting to a SAN do the trick?
 
Alternatively, would using 2x1GbE interfaces and using link aggregation be a better option, at least to the workstations?
 
I'm trying to keep the costs down as much as possible, and I am aware that the server storage write speeds will be an other issue to consider, but I am just looking for feasibility of and arguments for and against using fibre for ethernet style connectivity.
 
If you're talking about using fibre connections to SAN storage (HBAs), then you don't assign an "IP address" for this to work. The storage is zoned for the machine based on the path to the HBA and assigned a world-wide-number (WWN). The overall thought process behind how they work, again assuming you have the correct switches and are using some sort of ATA based SAN storage, is similar to normal network routing.
 
As far as fibre versus link aggregation, that depends on your preferences. Link aggregation will require setup on the switch side as well, and you need to be sure your switching infrastructure can handle it (as well as have your network admins, or you, be able to setup the LACP groups correctly). However, a 2GB aggregation will not be able to touch the total throughput of a dual-path fibre connection. Again, it's up to your requirements and which technology you feel more comfortable with as far as setup and maintenance.
 
Where I work, we use both, primarily (on the Unix side) for backups. We have 8x1Gb links setup for our backup media servers to accept incoming backup requests from many, many servers. The data is stored locally on staging disks, and then pushed out to long term ATA storage or tape using 2-3 dual path'd HBAs (fibre). They both have their place, and when used in tandem you can really reap some of the benefits.

---

### Post by spynappels on 2011-06-08
Thanks for that, I think I get most of that, but I suppose what I was asking (rather badly) was whether a fibre connection could be used like a standard GbE connection for faster networking. I guess a HBA would not work though....

---

### Post by blind2314 on 2011-06-09
> **spynappels said:**
> Thanks for that, I think I get most of that, but I suppose what I was asking (rather badly) was whether a fibre connection could be used like a standard GbE connection for faster networking. I guess a HBA would not work though....
 
 
This is possible, since that's how fibre ISP's deliver service to their customers :)
 
However, I'm not sure of how to set it up, since I've never had personal experience with it. I'd imagine it's just a matter of finding a switch that will accept fibre connections and then run the ethernet from their to your machines. However, running "networking services" directly to a machine via an HBA is not possible (at least..not that I know of). You'll still have to run ethernet cables to the machine at some point, which means you'll lose the speed benefit of using fibre unless you use link aggregation.

---

### Post by capscrew on 2011-06-09
> **spynappels said:**
> Thanks for that, I think I get most of that, but I suppose what I was asking (rather badly) was whether a fibre connection could be used like a standard GbE connection for faster networking. I guess a HBA would not work though....

I assume you are not talking o Fibre Channel HBA's which are for storage devices, but rather you are looking to connect hosts on a network with NIC's that use fiber cables.  You most certainly can use fiber GbE NIC's and cables.  It won't be any faster than copper though.  Just the physical equipment would be different.  You would still be using Ethernet and TCP/IP on the system.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.google.com/search?q=fribre+hba&btnG=Go!#hl=en&sugexp=ldymls&pq=fiber%20nic%20ethernet&xhr=t&q=fiber+nic+gigabit+ethernet&cp=18&qe=ZmliZXIgbmljIGdpZ2FiaXQgZXRoZXJuZXQ&qesig=904D0xMjKHpTUMRC_H7kQA&pkc=AFgZ2tmLROEAju2SzbWb57Oxr5g0VDt-OrpeqwMOI-ZfI9EZpCZMhw57lm-YR7whoFtPCSs5vxz9qmg8TtYZ0-04p1NTV00pLQ&pf=p&sclient=psy&biw=1167&bih=645&source=hp&aq=f&aqi=&aql=&oq=fiber+nic+gigabit+ethernet&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=b26a26caaf076322") for ideas. 

You can bond NIC's if the NIC and the switch allow allow for that sort of thing.  Remember that there are several types of bonding,

---

