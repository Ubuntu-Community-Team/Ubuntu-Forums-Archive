---
title: "Home Made Server"
date: 2010-11-03
forum: Server Platforms
---

### Post by razor7 on 2010-11-03
Hi, I'm planning to assemble a home made server for my enterprise, I'd like to have an Intel Core i7 or multicore Xenon but I dont have mouch expertise on server mothers and brands.

Can anyone guide me to build a homemade server?

I need to know:
    Wich processor should I use?
    Which motherboard brand choose?
    To have RAID 1, do I need to buy an external RAID card?
    Which HDD should I seek?
    What about power sources and desktop cases?

Of course, every hardware component must be compatible with ubuntu server

Thanks a lot in advise?

---

### Post by arnavk007 on 2010-11-04
how many clients would you have ??
also budget

if the no. of clients is small and needs are small then i think  a quad core desktop proccy with 4 gigs of ram and ample disk space should do.
otherwise look at six core proccys and if having the need and budget go for 2x six core opterons with 16 gig ram

---

### Post by noway2 on 2010-11-04
The big questions are how many users and what do you want to do with it?

A while back I bought a cheap desktop PC and have been using Ubuntu server on it.  It serves as a mail server, web server, DNS, DHCP, Samba, etc.  If you are looking for a home server for yourself, don't bother with expensive server hardware, it isn't necessary.

---

### Post by razor7 on 2010-11-04
Hi. it must server 15 users tops and be budget oriented.

What do you think of Xeon x3430, Intel s3420GPLC, 8 GB ECC RAM DDR3 1333 Kingstom, 500w power supply, 4x 500GB HDD RAID 5.

Thanks a lot in advise!

---

### Post by arnavk007 on 2010-11-04
^^^^^^^^
Is this budget oriented???

For Advice :-
if you wanna buy a new one
intel atom desktop board d510
2 gig ram
whatever is the hdd limit of intel atom and your case and other things
software raid would suffice

if you have an old one :-
then have a core2duo or somethin like that

if you have the monies:-
AMD Athlon x4 615e / athlon x4 645
4 gig ram
amd 880g chipset
again hdds are your choice

I think this athlon would work fine

---

### Post by CharlesA on 2010-11-04
> **arnavk007 said:**
> ^^^^^^^^
Is this budget oriented???

For Advice :-
if you wanna buy a new one
intel atom desktop board d510
2 gig ram
whatever is the hdd limit of intel atom and your case and other things
software raid would suffice

if you have an old one :-
then have a core2duo or somethin like that

The Atom would be a bit underpowered for such a system.

No room for upgradability (and no hardware virtualization).

@razor7: That hardware should work fine.

---

### Post by razor7 on 2010-11-04
By budget oriented I mean u$s1500, any brand new server from HP, IBM or Dell costs a lot more...

Thanks a lot!

---

### Post by arnavk007 on 2010-11-04
oh in thaaaat much
u can get :-
amd phenom x6 1090t
16 gig ram
890fx based mobo
a good case 
and hdds are again your choice

this setup will handle 100 clients easily

if you want a branded desktop then get a dell xps 7100 and customize it

---

### Post by CharlesA on 2010-11-04
> **razor7 said:**
> By budget oriented I mean u$s1500, any brand new server from HP, IBM or Dell costs a lot more...

Thanks a lot!

Really? I've seen some decent entry level servers for Dell that are fairly cheap.

You could assemble something from parts for that amount of money.

---

### Post by razor7 on 2010-11-04
Thanks a lot, but i need to provide the same characteristics of a branded server...(ECC RAM, RAID 5, VT-x).

Does the Phenom processors support ECC ram?
> **CharlesA said:**
> Really? I've seen some decent entry level servers for Dell that are fairly cheap.

You could assemble something from parts for that amount of money.
Hi, i have seen Dell Poweredge T110 in dell argentina, but adding all the needed ram, the hdds and without any raid solution the cost raises to u$s 2200!!!

Thanks a lot!

---

### Post by CharlesA on 2010-11-04
Most desktop processors do not support ECC.

You'd need a server class board and CPU.

---

### Post by SeijiSensei on 2010-11-04
> **razor7 said:**
> Hi. it must server 15 users tops and be budget oriented.

What do you think of Xeon x3430, Intel s3420GPLC, 8 GB ECC RAM DDR3 1333 Kingstom, 500w power supply, 4x 500GB HDD RAID 5.

Thanks a lot in advise!

Frankly an old Pentium 4 could handle 15 clients and not break a sweat.  What matters most is the speed of the hard drives and the amount of memory involved.  Serving files, web pages, and mail are all light-weight tasks, and none of them is compute-intensive.

I'd go with a [Dell T110 or T310]("http://www.dell.com/us/business/p/poweredge-tower-servers") myself.

---

### Post by razor7 on 2010-11-04
> **SeijiSensei said:**
> Frankly an old Pentium 4 could handle 15 clients and not break a sweat.  What matters most is the speed of the hard drives and the amount of memory involved.  Serving files, web pages, and mail are all light-weight tasks, and none of them is compute-intensive.

I'd go with a [Dell T110 or T310]("http://www.dell.com/us/business/p/poweredge-tower-servers") myself.

I forgot to mention that will run two VMs, one with OpenBRavo ERP, and the other with Alfresco Colaboration Suite.

Best regards!

---

### Post by CharlesA on 2010-11-04
> **razor7 said:**
> I forgot to mention that will run two VMs, one with OpenBRavo ERP, and the other with Alfresco Colaboration Suite.

Best regards!

I'm running anywhere from 4 to 8 VMs on a Dual core box with 6GB of RAM. 

Generally you'll want one core for each VM, and one for the OS, but mine's been running fine.

---

### Post by oldfred on 2010-11-04
Processor is not critical as nothing is CPU intensive. But more RAM speeds things up and RAID 5 with lots of drives insures things stay up.

But I do not see any data backup in your system?? Do you have legal requirements for emails. Financial requirements for data? You need to have a system for backup and off site storage of backups.

What power backup are you providing?? You at the least need enough battery power to be able to do a normal shutdown.

---

### Post by razor7 on 2010-11-04
Hi!, thanks a lot for all the advisory.

I'm seeking this config, what do you think?

[LIST]
[*]Case Codegen 9011 Server Case
[*]PowerSource COOLERMASTER Extreme 600W Dual Rail
[*]Processor Intel Xeon X3430 Quad Core
[*]MOTHERBOARD INTEL S3420GPLC
[*]Kingston 8gb Server Kit Ddr3 1333 240pin Ecc
[*]4x HD 500GB SATA2 WD Caviar Blue
[*]Cooler Bxsts100a Xeon
[/LIST]

> **oldfred said:**
> Processor is not critical as nothing is CPU intensive. But more RAM speeds things up and RAID 5 with lots of drives insures things stay up.

But I do not see any data backup in your system?? Do you have legal requirements for emails. Financial requirements for data? You need to have a system for backup and off site storage of backups.

What power backup are you providing?? You at the least need enough battery power to be able to do a normal shutdown.

So i need at least one UPS?

For backups i will be using our old 80gb desktop server to do backups over ethernet, and if it is possible, offsite backups through FTP.

---

### Post by CharlesA on 2010-11-04
> **oldfred said:**
> Processor is not critical as nothing is CPU intensive. But more RAM speeds things up and RAID 5 with lots of drives insures things stay up.

But I do not see any data backup in your system?? Do you have legal requirements for emails. Financial requirements for data? You need to have a system for backup and off site storage of backups.

What power backup are you providing?? You at the least need enough battery power to be able to do a normal shutdown.

Definitely things to take into account.

---

### Post by arnavk007 on 2010-11-04
good setup

---

### Post by CharlesA on 2010-11-04
> **razor7 said:**
> 
So i need at least one UPS?

Yes.

---

### Post by JDorfler on 2010-11-04
> **arnavk007 said:**
> oh in thaaaat much
u can get :-
amd phenom x6 1090t
16 gig ram
890fx based mobo
a good case 
and hdds are again your choice

this setup will handle 100 clients easily

if you want a branded desktop then get a dell xps 7100 and customize it

I have this set up, only an 890GX for on board graphics and 8TBs of storage.  I also have a Athlon II x4 running on a mini-ITX for straight media services.  I work on some older Enterprise style servers, and I can honestly say I'm not impressed with the whole thing.  Then again I'm a trunk level Data guy by trade.

Anyway, I want to get things going for Email services and Email collection from my commercial Email providers.

---

### Post by razor7 on 2010-11-04
Thanks a ot fopr the advise!

Will try to sell that config adding an UPS to be more shure.

Thanks a lot!

---

