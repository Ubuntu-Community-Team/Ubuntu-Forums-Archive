---
title: "hardware for virtualization"
date: 2008-07-12
forum: Virtualisation
---

### Post by optique on 2008-07-12
I just discovered this virtualization stuff and it is so cool!

What I also discovered is that the box I run Ubuntu on is too slow and old to virtualize Ubuntu. (But completely adequate for non-virtualization Ubuntu.)

So, looking to upgrade, would these choices in motherboard and cpu be good SVM choices? My short term objective would be to use Ubuntu to host Ubuntu, WinXP.

Motherboard:ASUS M2N-SLI Deluxe AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard - Retail 
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013")

CPU: AMD Athlon 64 X2 4800+ Brisbane 2.5GHz 2 x 512KB L2 Cache Socket AM2 65W Dual-Core Processor - Retail 
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103212]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103212")

I also plan 8GB ram. 

My present box is very old: AMD Athlon 1800 512MB ram. After hours of waiting for Ubuntu to install on QEMU, I aborted it. Seems like the graphics really slowed it down, although it was installing. 

But, I wanted to prove QEMU would work, so I downloaded FreeBSD 7, and it installed relatively quickly. (The install is not really graphical.) I was able to run it with no issue also. 

Seems like the buzz here is about VirtualBox instead of just QEMU. Why?

Thanks in advance for your help.
Steve.

---

### Post by Vadi on 2008-07-12
Virtualbox is easier to use for one. That's why I use it. I also tried KVM, which features a nice GUI for it, but for some reason or the other it was failing to install Windows properly (whereas virtualbox did for the same iso).

I'd recommend getting 2gb ram. 1gb for host os, 1 gb for guest os, and you'll be fine. While on your 512 it's understandable what 250/250 would bring slowness.

---

### Post by dark_phantom on 2008-07-12
Yeah, VirtualBox is pretty easy to use.  Also, the new VMware (Version 2 Betat RC1) is pretty good.  Now, most current CPUs are enable to do Virtualization.  If you pick any Core2 Duo processor it should be okay.  I suggest using at least 3 GB of RAM to run a pretty good VM.

---

### Post by optique on 2008-07-13
Thanks Vadi and Phantom for the replies.

Are my Athlon 64 x2 and my Asus motherboard good choices?

I was reading about Virtualbox; it sounds great. Any USB devices I have connected can be seen by the guest OS's, right? Assuming proprietary license...

Thanks.
Steve.

---

### Post by Vadi on 2008-07-13
Yes, they will be after you enable virtualbox to see them (you configure it in the settings. It's quite easy, just plugin in your device, and select it).

---

### Post by Shazaam on 2008-07-14
+1 for more memory on the host pc. I have an AMD Athlon XP3200 and 2 gigs of PC3200 ram and VirtualBox/VMware virtual machines run fine.

---

