---
title: "New Computer, Help with VMWare"
date: 2008-09-09
forum: Virtualisation
---

### Post by leodesol on 2008-09-09
Hi All,

I just bought this:

-----------------------

PowerSpec® E372

Processor
 Intel® Core™ 2 Quad Processor Q9300
 
OS
 genuine Windows Vista® Business 64 Bit edition
 
System Board
 Intel DP35DP
 
System Memory
 8GB composed of 4- 2048MB DDR2/800 DIMMS
 
Hard Drive
 1TB RAID 0 - (2 x 500GB SATA HDDs) 7,200 RPM
 
DVD ±R/±RW Drive
 Blu-ray ROM / DVD± / ±RW Drive
 
Video
 GeForce 8800GT PCIe 512MB
 
Sound
 Integrated Sigmatel® 9271D 8 channel audio
 
LAN
 Wireless LAN G/B PCI Card
 
LAN
 Intel® Integrated Gigabit Ethernet
 
Software
 ESET NOD32 Antivirus Trial Version, Microsoft® Office 2007 Trial Version, and Adobe® Reader®
 
Firewire
 TI TSB43AB22A IEEE Firewire 1394 Controller
 
Memory Card Reader
 Media Card Reader
 
Keyboard
 Microsoft® Wireless Keyboard
 
Mouse
 Microsoft® Wireless Optical Mouse
 
Warranty
 1 Year Limited On Site Warranty
 
----------------------------


It is a nice machine. Especially nice in that it came with Windows XP Pro preinstalled and a Vista Business upgrade disk.

So, the first thing I want to do is install Linux as my primary operating system of course. This should be fairly easy to accomplish.

The real question is if I can use VMWare or some other program to get both this Windows XP Pro licensed on a VM and get VISTA Business edition as another VM too? Any good guides for doing this type of thing too? I am new enough with Linux and have really never setup VMs much yet.

Keep in mind, I get to create recovery DVDs for XP, and have an Upgrade DVD for Vista Business. If I have to choose to VM one or the other because of license issues, I'll probably go with Vista for 64bit gaming.

---

### Post by bodhi.zazen on 2008-09-09
You will find tons of information in the virtualization forum. Start with the stickies.

Personally I advise you go with KVM :

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I ran qemu for some time so personally I find it easier to run from the command line. At any rate, use a physical partition and install windows into it.

You can try to do the same with VMWare.

The trick here is to install windows using KVM / VMWare rather then booting to a CDROM => installing windows => then trying to boot the partition with KVM or VMWare.

---

### Post by plonka2000 on 2008-09-10
Just out of interest, but are you looking to play games out of a Vista VM? I noticed you mentioned that you wish to use Linux as your primary host OS. Personally, I wouldnt recommend it (Gaming from a VM that is).

---

### Post by leodesol on 2008-09-10
Yes. I was hoping to game on VM, not all games, just the ones without good Wine, etc. support. Now, after taking the advice of reading the virtualization forums I am just going to dual boot. I am going to do most of my space to Linux, keep about 100 Gig to Vista, then play with the different VM options to see which I like. I also want to use VM not just for gaming, but for trying other Linux systems, making Windows/Linux servers, and also have an XP partition so that I can use my office 2003 on it (will use Open Office too though).

---

### Post by plonka2000 on 2008-09-10
Dual booting sounds like a much wiser idea for your purposes.
If you want to game, unfortunately there is still currently no better option that running a native Windows install. You'll need the direct access to the hardware for running 3D and using DirectX with your hardware graphics card, etc. When you're done fragging, then you can just reboot and be done with it again too.

Also, in my experience Windows runs smoother the less you install on it, so just having a purely gaming installation of Windows is much better than a general purpose system that is also used for gaming. That just ends up getting slower and slower and Windows strangely seems to do.

Still, no better platform for gaming currently.

---

