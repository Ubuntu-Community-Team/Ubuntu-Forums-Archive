---
title: "Rig for KVM/Virtual servers"
date: 2008-06-28
forum: Server Platforms
---

### Post by gurkburk on 2008-06-28
ATM im trying to complete the hardware for my new personal server rig at home.
What im focusing on atm, is the amount of RAM.
Im going to run some form of virtual server system, interested in KVM atm (will most likely just run multiple ubuntu server's, not different distros or so).

CPU will be AM2, there will also be a heavy amount of discs in the machine, 2 for system in raid0 and 4-5 (for starters) in raid5 for storage. The storage will simply grow with time, I have space for about 13 discs in the case altogether.

Now, if I wanto just have hobby-stuff on it I would most likely just put 2 cheap 1GB sticks in it and be happy, however I wanto run it with kvm (probably) in the base and have virtual servers on it (I dont 'need to' now, just wanto have the possibility and dont hafto start over later).

For now it will run the usual stuff, webserver,mysql (no real load.. 10 users per day tops, ventrilo (few users), some torrent-downloading and whatnot.
Now, if I suddenly put up some game-server (COD4), it will need more juice.

I will go for a motherboard with 4xRAM slots, would it be future suicide to just put 4x1GB in it?
Its not really a cost-issue, just that as a regular windows-joe user, ive never even had an OS capable of using heavy amounts of ram.

Perhaps Ill go with the 2 1GB sticks I have, and get 2 more 2GB  sticks in, that way the machine will have 6GB to play with, should be enough for starters.

(Figured I can use 4GB for the "main" virtual server and 1gb each and have 2 more virtuals for experimental use).

Thoughts?

PS: Still havent found a good motherboard to be honest, not one that fits all my requirements.
What I want is AM2, builtinVGA, 3xPCI (minimum), 6xSATA(preferably) and 4xRAMslots... not alot of cards out there it seems.

---

### Post by Uluen on 2008-06-28
Unless you already have the CPU, try getting a decent server-ish motherboard, ASUS P5M2-M for example.

Good chipset:Intel 3000 MCH/ICH7R, good NICs: Broadcom (not the Realtek junk), 2x PCIe etc etc.

I'd start with 2x 2GB RAM and use a single disc for the system.
If money isn't a issue, have a look at LSI Megaraid 8+ port SAS/SATA controllers.

---

### Post by windependence on 2008-06-28
I am an AMD man myself and an AMD partner. I would use a Tyan or SuperMicro board. One thing you will want to make sure is that you have a GOOD power supply. On that box, I would recommend 600w or higher and preferably 800w.

For me, I like VMware server better than KVM because of the flexibility. I have a dual quad core Operon server I just built using a SuperMicro H8DME-2 Motherboard, and 12 gigs of RAM with 1.5 Terabytes of storage. This board has an on board SATAII RAID controller with 6 ports.

VMs like memory so don't be shocked if you need more. I would say a minimum of 4 Gigs. Use 2 GIG DIMMs, they are cheaper per gig anyway. On those boards you also need ECC Registered RAM.

Let me know if I can be of any more help.

-Tim

---

### Post by gurkburk on 2008-06-30
Been rethinking the hardware abit, gone from an AM2 (the one I had "lying about") to an AM2+ Phenom 9850 (quad 2.5Ghz 4mb) on an ABIT AN78GS, with 4x2GB sticks for 8GB ram.
This gives me a decent rig I think, I have space for my GBit Intel-NIC, builtin VGA, 6-SATA on board and 2 PCI-slots for extra promise-cards.

The Tyan cards are very nice, supermicro aswell, its just a huge price-difference, and in the end, its just a hobby-server that I will host at home.
Going from a "regular" AM2+ setup, to a dual opteron on a tyan-card rises the price about 10 times.
Even though I pay for it through my own company, its still my own money  im spending :-p

But ive raised the specs on motherboard,cpu,ram and psu so faar to be sure to have enough juice in the end.

Thanks for the inputs :)

---

### Post by gurkburk on 2008-07-05
Still havent exactly decided, having a hard time putting all this hardware running with a "normal desktop" motherboard, even a high-end one, its still a regular motherboard, which is why im having 2nd thoughts on the phenom-cpu.

Been looking somewhat at a 771-motherboard from asus, Asus DSBV-DX, I5000V. Takes 2 Xeon-cpu's, and 6 slots of ram, builtin vga and proper intel gbit NIC's. Thought id rig it with 2x1.6 Xeons.

I havent been able to find/configure a similiar build with AMD-components, but perhaps someone could recommend a board and cpu's?

I wouldnt mind getting my hands on a AM2+ or dual AM2+ motherboard for servers, but havent spotted one myself.

---

### Post by windependence on 2008-07-05
Tell me what your budget is. I can suggest some things as I am an AMD channel partner.

-Tim

---

### Post by gurkburk on 2008-07-06
Well I dont exactly have a budget, im just trying not to over-spend because I have other things to put money on and, this is "just a home-server" for myself, im just fed up with having a 24/7 server at home with heavy stuff in it, but having the foundation consist of a regular desktop motherboard/cpu that always fails in the end.

Looking at a dual Xeon motherboard (the asus DSBV-DX), and 2x1.6GHz Xeon 5110 4mb, compared to a "top of the line desktop" motherboard, with a phenom these numbers are comparable:

Asus DSBV-DX and 2xXeon 5110 runs me around 920$ just for board+cpu's. 
Compared to a gigabyte-card+phenom 2.5ghz which ends up at 570$.
However, im willing to spend 450$ more, not because I think I get more juice out of the xeon system in any way, simply because I get a motherboard that was built for servers that I think could last alot better in my rig then some gaming-board.

So budget, perhaps around 1000$, aslong as I dont overshoot to much I suppose.

Note: Im not from usa, just compared prices and did a forex-check on dollar-prices and divided my sums... so perhaps your retailer-prices are off a but, not sure, just to give you a ballpark of where im thinking off putting my money.

Its all going into a chieftec smart wh01-case, for starters ill use a 750W Corsair, going with 8(4x2)GB ECC memory, for system-discs I got 2 SATA-disks, and ill put 4 or 5 500GB in raid-5 for starters, then ill add discs to that raid as I need to, which wont be very soon, but I will be able to have 10 500gb's in that raid before my space in the server runs out.

That's also something I like about a heavier motherboard btw, as with any regular board for home-use, your are limited (in 99,9% of the cases.. 100%?) to 4 ram-slots, which does not apply on serverboards. The xeon-one ive been looking at has 6 which means I can add pretty much 2, 4 or 8gb more ram later, and I seriously like that idea.

So any server-board for either a phenom, perhaps dual opterons, with vga/lots of ram-slots and hopefully atleast 4 sata-slots, im interested in.
And ofcourse I can spend more then 1000$ on board+cpu, if its a dual-one I can just spend 1000$ on motherboard and 1 cpu, and add an extra cpu later when I need the juice.

Thanks for taking your time helping me out, looking forward to your suggestion.

Edit:
The big difference in what hardware im going for now compared to what I started with is ive decided to replace 2 servers and 1 stationary (that just functions as a server more or less), with this "one and only" server, with virtual server-capability for the future (I wanto put up a server for labtests every now and then for example).
Think it looks weird going from a left-over cpu and budget-card to this xeon/dual opteron solution, so figured it took some explaining ;-)

---

### Post by windependence on 2008-07-06
Well, unfortunately you can't make chicken salad out of chicken sh*t. I am not a big Asus fan and even less of an Intel fan. AMD has the best dual and quad cor architecure out there, I don't have to tell you. 

That being said, I don't see any way around buying good server class hardware. The Tyan and SuperMicro boards I suggested have 8 memory slots, on board SATA RAID and some other nice features, but they cost $300-$400. And then there are the processors to populate it. I just built a dual quad core Opteron box like this and it cost over $2,000 and I am a reseller, not a retail customer. Should you decide you need that type of hardware, I do ship over seas BTW. 

Let me see if I can find you a high end desktop baord that supports AMD processors. Maybe something like the graphic designers use.

-Tim

---

### Post by gurkburk on 2008-07-06
Well, ive always prefered the Tyan products just never build a rig with it for myself.
Checked some dual 940-boards out, the K8WE looks nice, comes with an optional builtin VGA which sounds sweet, 4 SATA which fills my minimum-requirement, and 6 slots for ram.
Putting one opteron 248/2.2GHz in it, brings it to around 1-1100$, which I guess will hafto do. And I always have the future option of putting another 248 in it, and additional ram.

Going to do some more reading, and check a couple more boards out and check with the resellers I usually buy stuff from, but think I will be happy with the tyan-opteron setup, even though I like the xeon-cpu Ive always been more of an AMD-man myself ;-)

---

