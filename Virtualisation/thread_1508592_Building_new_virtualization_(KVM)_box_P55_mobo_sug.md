---
title: "Building new virtualization (KVM) box: P55 mobo suggestions"
date: 2010-06-13
forum: Virtualisation
---

### Post by koala15 on 2010-06-13
I am going to buy a new box to host KVM  virtualization (running Ubuntu as host and (multiple) Ubuntu and Windows  as clients).

My main consideration in this post is the mobo.

The cpu will be intel i7-860 or similar (ie LGA 1156). So the mobo needs to be a P55 chipset, I think.

I have considered

[LIST]
[*]Gigabyte (the GA-P55A-??? series),
[*]Asus (P7P55D series, the "PRO" being my pick), and
[*]EVGA P55 series.
[/LIST]

After reading a heap of reviews, I have no great preference but I like  the EVGA P55, and EVGA P55 FTW.

My major consideration (obviously) is 100% support for Ubuntu. The EVGA  mobo has rave reviews, but I can not determine its compatibility for  Ubuntu, as EVGA do not supply Linux drivers with the board, and I have  searched for anyone with Ubuntu experience on the board, without  success.

Could you please supply your thoughts especially from your practical  experiences. Thanks.

I am happy to consider any rig, but it MUST be 

[LIST]
[*]LGA 1156 cpu capable,
[*](max) 16gb memory AND
[*](here is the very important bit) the mobo must support VT-x AND  VT-d.
[/LIST]

Thank you very much.

---

### Post by BobLand on 2010-06-13
I can't how you would have a problem with any computer.  I've run VB on a number of different machines with no problems.  If anything, make sure you have enough memory, I'd say at least 4 GB if not more.

I'm building a machine to run Sony Vegas 10.  It will be an I7-920 with at least 6 GB to start with 5 going to VB.  Since version 10 will use GPU I've decided to go with a GTX 470 as this has 448 cores.

Good luck

---

### Post by benderisgreat on 2010-06-14
> (here is the very important bit) the mobo must support VT-x AND VT-d.
For VT-d you need to look for Intel vPro support which comes with the Qxx chipsets. The Q equivalent for P55 is the Q57. As used in for instance the Asus' P7Q57-M DO or Gigabyte's GA-Q57M-S2H.

---

### Post by naelq on 2010-06-30
hi **koala15**,
any progress?

i'm in the same situation, building a virtualized-staging-box for my lab & would like to hear about your experience :)

---

### Post by sh1ny on 2010-07-02
If you're going to be serious about this, and if you'll run critical applications on those virtual machines, i'd suggest you buy a real server - either HP, Dell or Supermicro ( with the last being my personal choice, because of the price/quality ratio ).

Get a Xeon 5520 or better for cpu.

---

### Post by TheFu on 2010-07-03
> **sh1ny said:**
> If you're going to be serious about this, and if you'll run critical applications on those virtual machines, i'd suggest you buy a real server - either HP, Dell or Supermicro ( with the last being my personal choice, because of the price/quality ratio ).

Get a Xeon 5520 or better for cpu.

I saw a Dell 310 server for $499 earlier this week on a deal website. That is the smallest "server" that supports DRAC/RIBLO cards from Dell. A DRAC/RIBLO is a requirement for my needs.

I've had bad luck with E* motherboards. Gigabyte have always worked "for me."  I'm a single data point, so hardly useful.  If you ever think you may want to change to a different virtualization tech, like VMware ESX, then be certain to check the whitebox compatibility lists. ESX can be picky about non-server hardware and refuses to load with many desktop HDD controllers and NICs.

---

### Post by naelq on 2010-07-14
any progress with your build?


nael

---

