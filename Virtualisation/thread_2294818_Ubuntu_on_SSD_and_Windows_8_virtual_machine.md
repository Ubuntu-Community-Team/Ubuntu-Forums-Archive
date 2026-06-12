---
title: "Ubuntu on SSD and Windows 8 virtual machine"
date: 2015-09-13
forum: Virtualisation
---

### Post by ceiba.naku on 2015-09-13
Hello all,
I just got a new  ASUS ROG GL552J that I plan to use for scientific computing (mostly modelling population ecology in Python and R) for a PhD in marine biology. I currently have 12 GB RAM (hoping to expand soon) and a 500GB SSD. The machine has Windows 8 preinstalled, but I'm planning on installing Ubuntu onto the SSD and using the existing 1TB HDD for media and other files. Since I use Ubuntu for 99% of everything, I'm considering eliminating the current Windows install and instead running windows through a virtual machine. I only use windows on occasion, and usually for hefty software like Statistica or SPSS. Does this seem like a good idea? I have used a dual-boot system before, but ended up duplicating a lot of files since windows couldn't access the Ubuntu partition. My technical experience with this sort of thing is still limited, so I'd really appreciate any advice :) Thanks in advance!

---

### Post by QIII on 2015-09-13
If you are planning to buy a new retail version of Win 8, it's a great idea.

If Win 8 was preinstalled, it is activated against the machine it is currently on.  A virtual machine is a different machine.  It will be running on the hardware abstraction layer provided by the virtualization layer and not on the physical hardware it is currently tied to.

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **Virtualisation**.*

Sounds like a fine idea. You have plenty of RAM and that is the main thing. When you installing a virtual machine you need to allocated it some RAM. The host and guest can share your installed RAM.

So 4Gb for Windows and 8Gb for Ubuntu or 6 each or whatever you choose. If what you're doing in the virtual machine is fairly inconsequential resource wise, go for 2Gb of RAM and 10Gb for the host (Ubuntu). 

Hope that helps. :)

* And QIII makes a good point. You'll need install media or the ISO for Windows. That needs to be installed as guest OS in Virtualbox or another app with Ubuntu as the host OS.

---

### Post by ceiba.naku on 2015-09-18
Thanks! I was afraid of the whole "new license" thing, but I guess I would be willing to do it if it's a better solution :( I would hypothetically be using windows for resource-intensive work, so I was thinking of allocating 12 GB to the VM and 4 GB, assuming the machine RAM maxes out at 16 GB. Would that be feasible? Otherwise, is there a way to get the two systems to play well together as a dual boot? My main problem with it was having to boot up again just to use one program, and having to duplicate files just to do simple things. Also, backing up two systems and keeping them in sync ended up being messy. I've thought about making the HDD a big, shared NTFS partition with media files, but I'm not really convinced by the idea. I like having an encrypted home folder in Ubuntu, and generally prefer to have everything running through a more secure and trustworthy system. Any opinions? Thanks again!

---

