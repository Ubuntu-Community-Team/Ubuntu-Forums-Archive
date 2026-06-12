---
title: "Provisional spec for virtualization"
date: 2009-03-08
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-08
Hi

Thanks to every one who replied to my earlier post requesting help choosing a visualization package etc.

I have now arrived at a provisional spec for what I hope to do and would be grateful if anyone can spot any flaws before I commit to it: -

Server: - 

Dell Poweredge R200
Dual core Intel Xeon 3Ghz
4 gig of ram
2 x 250 gig raided hard drives Raid 0

I want to install Ubuntu 8.10 Server Edition as this has KVM built in and I want to run several virtual servers and PC's on this machine; each configured to appear as machines on my network. I am hoping that by the time I have figured out how to install and configure everything I will be able to do the following: -

- Run two virtual Ubuntu server instances, one as an application server the other a database sever. This would then become a development environment for me.
- Run a Windows XP PC purely to host my copy of Adobe Photoshop.
- Switch on or off any individual instances of the above.

I am also planning to take a look at writing device drivers in the near future. My initial impression is that this may mean modifying and recompiling the Kernel. I would prefer to risk screwing up the kernel of a virtual instance of Ubuntu than my installed version so I am hoping the virtualization route will prove a good idea in this respect.

Any comments would be much appreciated.

Thanks

Brad

---

### Post by mrsteveman1 on 2009-03-08
RAID0 as the basis for a servers storage is asking for trouble. Use RAID1 or get another disk and make a RAID5 array.

---

### Post by BradleyAtkins on 2009-03-09
Yes I wondered about that.

It is being offered with raid 0, does that mean it is capable of supporting raid 1? I am not sure if I can order it with raid 1 but would prefer it so would need to configure it myself I guess.

For my need 250gig is fine so I don't mind doubling them up.

---

### Post by mrsteveman1 on 2009-03-09
Are you ordering a custom colocated server from a company or is this coming from dell? You should be able to do whatever you want when you get it, but there isn't any reason they can't do the raid1 for you either.

---

### Post by BradleyAtkins on 2009-03-10
Thanks Steve

Turns out they do have an option to RAID 1 it so I have gone for that, also ordered the RAID documentation in case I decide to change it.

Now I just have to grit my teeth and wait up to 10 days for the thing to arrive.......

---

