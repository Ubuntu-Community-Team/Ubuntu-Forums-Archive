---
title: "Help configuring new server with RAID"
date: 2007-01-23
forum: Server Platforms
---

### Post by Barleyman on 2007-01-23
Hi, I am considering buying a new server for my small home business.  

I have researched many servers and found [this one on newegg.com](http://www.newegg.com/Product/Product.asp?Item=N82E16856152019) that seems to be a very popular well reviewed entry level server.  

I am considering getting that barebones kit with 2GB ram, 4 SATA 320GB HDs, a AMD Opteron.   

My plan is to use it with vmware to run two virtual servers, one with trixbox (asterisk) for my pbx and one for samba server and have room to add another virtual server for testing/playing around.

Two questions, does this solution seem reasonable, and what would be the best way to setup and configure software raid for this system that enables maximum storage space?


Thanks in advance, John

---

### Post by hardwarehank on 2007-01-23
Hi there.  Do you want redundancy?  I would recommend RAID5 (I use it) because it allows one of your drives to fail.  It requires at least 3 drives though, and you only get to use (n-1)/n of your space, where n is the number of drives.  So for three drives, you get 2/3 of the total space.  A better way to think about it is you lose a drive to parity.

If you want max storage, RAID0 is what you're after.  Look into **mdadm** to set either one of these up.

---

### Post by Barleyman on 2007-01-23
Thanks hardware hank,

Yes, I should have stated my request a little more clearly.  I am mostly concerned with redundancy.      

I have been reading as much as I can about software raid and linux, but one thing I cannot figure out is how best to set up RAID5 with only 4 drives.  Can I have the OS run on the software raid, or is this a chicken and egg problem?

Does it make more sense to do this 

Optiion1
1 80GB-250GB SATA drive with no raid for OS.
3 320GB SATA drives for the RAID5.

or 

Option 2
4 320GB in software RAID 5 for the OS and.

What is the best way to partition everything?   In option 1, what happens if the OS drive fails, can I just pop in a new drive with a fresh OS install and it will detect the preformatted software RAID 5?

---

### Post by Barleyman on 2007-01-24
any advice for option 1 or 2?

Optiion1
1 80GB-250GB SATA drive with no raid for OS.
3 320GB SATA drives for the RAID5.

or

Option 2
4 320GB in software RAID 5 for the OS and.

feel free to rail on me, I am really new to setting up RAID.

---

