---
title: "home file server"
date: 2010-01-13
forum: Server Platforms
---

### Post by pyn on 2010-01-13
I'm planning on setting up a home file server. I was wondering what platform would be recommended for something like this. The server would be used mainly for media storage which would be shared between an HTPC and a couple desktops and laptops. I was thinking of just getting whatever motherboard had the most SATA headers on it (which currently seems to be something P55-based) and setting up a RAID5 fakeraid with some 1.5 or 2TB drives and the OS in RAID1 with whatever drives I have laying around. It there anything flawed with this approach? P55 boards with 10 SATA headers are currently upwards of $200, which is kind of pricey. Is there a more economical route that I should consider? Also, are there any known problems with setting up a fakeraid like this using certain motherboard's SATA controllers? Thanks!

---

### Post by falconindy on 2010-01-13
Fakeraid is known to be problematic. There's plenty of posts on these forums alluding to installation issues with Fakeraid. It seems to be particularly common with the nvidia chipset that the RAID members are recognized individually as if the controller wasn't enabled in the BIOS.

Look into MDADM and LVM as a more robust solution.

---

### Post by Fcon_Vpro on 2010-01-14
What falconindy said... I recommend MDADM.
Also as far as I know, most intel fake raids only allow you to raid 4 drives max.
Also those 10 sata ports will be on different controllers so you wont be able to raid all the drives together on fakeraid.

MDADM will allow you to raid as many drives as you want regardless of which controller the port is or whether your motherboard supports fakeraid (ie mdadm can turn any sata port into raid). So if you went with the 10port motherboard, MDADM can combine all 10 ports into 1 array.

A cheaper option may be to buy a cheap 6port SATA motherboard, and buy add on 4 port sata controllers for PCI or PCIe.

I would recommend you go with either RAID5 or RAID6. 
RAID10 uses too many drives for redundancy and I dont think it is worth it.

Hope this helps?

---

### Post by pyn on 2010-01-19
thanks for the replies!  I will look into MDADM.  does the other logic surrounding my server build sound correct?  are there any considerations that I might have missed?

---

### Post by Fcon_Vpro on 2010-01-19
Everything else sounds fine that you mentioned. Raid1 OS setups are sometimes tricky to setup but if you know how to, then go for it.

I currently run my Ubuntu OS on a single drive because it is so easy to get my system up and running again. Literally its as easy an installing the OS, installing MDADM and MDADM automatically locates my array and adds it to the system. Only when you create a brand new array do you need to manually add it to the mdadm config which is easy (see tutorial link at the bottom)

MDADM is really amazing. Ive moved my array between 3 different variants of Ubuntu on different hardware setups. The raid info is stored in the superblocks of the drives, so you can swap your hdd's on sata ports, etc and the array will pick up everytime. Ive also grown my array from an initial 2TB's to 3TB's, then recently to 7TB and now 8TB.

This is an awesome guide to setting up RAID5 with MDADM
[http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

---

