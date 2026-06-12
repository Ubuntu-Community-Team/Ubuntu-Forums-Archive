---
title: "Can You Advise - More CPU or RAM"
date: 2015-05-04
forum: Virtualisation
---

### Post by Quarkrad on 2015-05-04
I hope you can advise - I'm running 14.04 on an i3 machine with 4GB ram and having trouble with the performance of this host when running virtualbox (normally when win 7 guest is running).  Attached picture of my resources - is this telling me that my ram is OK but I'm bottoming out re my cpu capacity?  I.e. I should look at maybe an upgrade to an i5 cpu.

---

### Post by 1clue on 2015-05-04
Try allocating more memory to your Windows guest.  Not only do you have to worry about swap on your Linux box, but each guest usually has swap involved as well.

Is your memory expandable past 4gb?  If so, it never hurts to get more.  To me, running a VM on a box with only 4gb is problematic but my use case is possibly very different than yours.  For me, I'm sunsetting a box with 8g because it can't be expanded past that.

Also, please show us the filesystems tab.

---

### Post by 1clue on 2015-05-04
Also, on the first tab you'll see a process list.  Get it into a slow state again, and then look at the process list.  The thing that's eating the most CPU will have a higher number in the CPU load column.

---

### Post by Quarkrad on 2015-05-04
Here is my file system tab.

---

### Post by 1clue on 2015-05-04
OK nothing really alarming there, other than the windows filesystem being mounted.  Do you need that?  If not, then you might consider making that not mount automatically.

---

### Post by mastablasta on 2015-05-05
give at least 2 GB to the guest OS and dedicate a core to it. should be better... also turn off any special desktop effects (aero) that use hardware GPU acceleration. I believe that win 7 can have that classic win98 look with minimum GPU hardware acceleration needed (if any).

---

### Post by Quarkrad on 2015-05-05
I currently have 1GB ram allocated within the vm - use to have 2GB but read that it is best to have 1GB only (again, confusing advice on the net and hard to work out what is best).  Also, I do not know how to dedicate a core to the vm - I'm guessing you dedicate a core to Virtualbox.  I have had a search on how to do this but again - confusion.  Are we talking about the number of cores allocated in the vm set-up (I don't think so) or a setting outside virtualbox?

---

### Post by Bucky Ball on 2015-05-05
*Thread moved to **Virtualisation**.*

Settings in the VM when you are setting up the client OS, not outside of Virtualbox or whatever you are using. You allocate x amount of RAM and y amount of CPU. In your case, one core. 

I have exactly the same specs, i3 and 4Gb. I can run a VM with one core and 2Gb RAM faultlessly (although not Win7 so that's pretty redundant info!). ;)

Hopefully you will have the same experience. 1Gb of RAM for Windows 7? Dubious. Would that run well natively on a machine with 1Gb of RAM? Don't use, so don't know, but guessing not. 

This is what Win7 (regular, not Pro) needs, according to [this]("http://windows.microsoft.com/en-AU/windows7/products/system-requirements") page:

> 1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit)

Another interesting note from that page, somewhat surprising:

> *Windows _XP Mode requires an additional 1 GB of RAM_ and an additional 15 GB of available hard disk space.*

... so doesn't look like that theory is going to save you. Just the opposite.

---

### Post by Quarkrad on 2015-05-05
Would it be possible to have a copy of your win7 vm settings so I can compare?  I attach mine.  Also, I have 64bit copy of win7 I could use - do you think using the 64bit version would make any (real world) difference to the existing 32bit vm?

---

### Post by 1clue on 2015-05-05
I have a Windows 7 image but not on a Linux host.  It's set for 2g RAM and 1 core.

I notice you have 'Nested Paging:   on' on your config, my setup has no changes to that but if your win7 is low on memory then swapping through the guest driver to the host can be worse than swap on the bare metal, depending on your hardware.

---

### Post by TheFu on 2015-05-05
So - I found 1.5G of RAM and 1 vCPU to be fine with Win7 32-bit, but it will depend on your workload. Mine is recording 4 HiDef video streams using Win7 Media Center and little else.  Occasionally, Quicken will be run.

Overall performance for a VM is more about properly sharing the available resources with the other VMs and hostOS.  That means making RAM sized to what is needed, no more.
vCPU sizes to what is needed, no more - though with Windows you have to reinstall if you change from 1 to (2 or more) vCPUs. Windows installs a different kernel based on the number of vCPUs at install time.
Then there are network drivers and disk drivers ... and of course, how the virtual HDD was created.   On an SSD, it doesn't matter, but for spinning disks, preallocating the storage (probably 60G) is advised.  Though recent sparse VDI file performance has improved, it isn't as good as fully pre-allocated storage on spinning disks.

If you want more tips on vbox setup: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

RAM looks fine. Appears your processes are CPU bound and single threaded. That means faster single-core performance is what you want. You don't need more cores.  With desktop CPUs, you can't use NEMA pinning for VMs.  I assume we are looking at the hostOS performance?  Really it would be better to run performance monitoring 24/7/365 on a VM server, so you can see issues that happen over months, not just 1 day.  Munin is really easy to setup.  Have it here on all are servers with a central box as the central hub.

Looking through the settings ....  
* video-RAM is too low for a desktop. 128MB.
* If this is running iTunes - there isn't anything anyone can do to make it perform better. You could have 16G of RAM and new Core i7. It will still suck. ;)
* Use ICH chipsets everwhere. This will require a reinstall.
* For storage -use ICH and SATA (or virtIO). virtIO is easy for Linux guests, for Windows, drivers must be installed.
* NIC should be Intel PRO/1000 or virtIO.  virtIO is easy for Linux guests, for Windows, drivers must be installed.
* Can't tell if you used sparse or fully preallocated storage or what the hostOS storage type is.

---

### Post by 1clue on 2015-05-05
For Windows you can break license agreements by adding cpu's (sockets) but generally not by adding cores.  Going from automatic delegation of cores as-needed to 1 or 2 full time cores will probably not hurt anything, as long as you don't touch the number of sockets.

I'm not arguing with TheFu, he's looking at your specific setup while I'm talking about license agreements common on Windows operating systems and software.

---

### Post by TheFu on 2015-05-05
I should point out that seeing the hostOS memory isn't really helping to know that the guestOS (win7) needs.  You really need to look inside the Win7 box at those performance numbers to see whether CPU or RAM or DiskOS or NetworkIO is the issue.

So - if you have 4G of RAM and you are running Win7 inside a VM limited to 1G of RAM, the hostOS will probably use between 1.5G and 2G of RAM - see how that works?  When you add more videoRAM to the GuestOS - that will hit the total RAM for the hostOS by an equal amount and the the hostOS RAM use will be 1.6-2.2G.  Don't forget that managing a VM takes about 100MB on the hostOS too.

For Windows, I haven't seen much performance difference between virtIO and SATA/IntelPRO1000 virtualized HW. On Linux, with Linux VMs, virtIO is easier to use, less overhead and faster.

Nested Paging - you can look up what that does. For KVM, nested paging can add 30% to VM performance by allowing hw to manage memory access for pages.  [http://developer.amd.com/community/blog/2008/02/20/boosting-kvms-performance-with-nested-paging/](http://developer.amd.com/community/blog/2008/02/20/boosting-kvms-performance-with-nested-paging/) For virtualbox, they only claim 5% improvement and only for Core i7 Nehalem [https://www.virtualbox.org/manual/ch10.html#nestedpaging](https://www.virtualbox.org/manual/ch10.html#nestedpaging) - would need to lookup specific processor models to see whether this helps in your specific situation or not. That last link lists the **modifyVM** commands to enable the settings. Be certain to check your CPU first for compatibility.  When it comes to tuning at this level, ALWAYS, ALWAYS, ALWAYS read the documentation and double-check that it applies to your specific BIOS, chipset, CPU and hostOS.

---

### Post by SeijiSensei on 2015-05-05
I usually find 1.5 GB is the minimum to run Windows 7 with decent performance.  On a 4GB Ubuntu machine, I'd give the Windows VM 2.0-2.5 GB.  Ubuntu is much more comfortable with memory in the 1-1.5 GB range than is Windows.

---

### Post by Quarkrad on 2015-05-06
Thank you for all your replies/advice.  I'm starting to think my expectations about performance is too high - to be honest, most of the time win7 performs ok and there is only the occasional slowing down/halting of my host (I normally play radio via firefox on  my host whilst working at the pc and there are quite a few occasions when the audio stops when the vm is doing something heavy - it eventually returns though).  One thing I am considering (interesting to see that upgrading to i7 and more ram may not improve performance), having read it a number of times, is converting the dynamically allocated vm storage to a fixed size type.  Have you any real world experience of this - do you think I will see any improvement?

---

### Post by TheFu on 2015-05-06
It all depends on the workload.  I see 90% of native performance for the things I do with the settings listed in the slowVbox link above. If you don't follow the settings outlined, you really don't know what performance level of which your hardware is capable.  The most important settings are in post #11.  The comment about itunes is about expectations. Certain programs are extremely heavy and perform poorly.  I've never seen iTunes perform well on any hardware.

What is your workload?

It is common to have a C2D running 5 server VMs and to see fine performance. Been doing it for years - using ESXi, Xen, and KVM.

If you are trying to play video or audio inside a VM, I would strongly suggest you find a native option to run on the hostOS. Sure, I run audio inside VMs, but it more as a novelty than something I'm willing to live with daily. OTOH, all my VMs are remote.  I don't even consider running video in a VM.

There are people here that run high-end games at 120fps, but they are going to great extremes to dedicate a 2nd GPU just to the VM, doing VGA passthru, patching kernels, and own very specific MB, CPU, and GPU hardware. Oh - and they use either KVM or Xen for virtualization.  I would just dual boot, if I needed that performance and couldn't allocate a machine (like I have).

---

### Post by Quarkrad on 2015-05-06
Thank you - I have actually created another vm following the advice here and on your blog.  I'm afraid my use of win7 is purely for itunes so I am stuck with the issue re performance you have mentioned.  Apart from itunes I have migrated completely to Ubuntu - a few years ago I was hoping Songbird audio player would replace itunes but that app. dropped Linux and went win/Apple only.  Songbird has now disappeared and Nightingale looks to be the replacement.  Despite my reluctance re itunes, and a few issue I have with it, it is a good piece of software and will be around as long as Apple is around so I guess I will have to keep win/itunes for the stability it provides.

---

### Post by TheFu on 2015-05-06
OT - DRM RANT

I loaded iTunes once - it was forced on me with Quicktime years ago - lasted less than a day. Decided that quicktime wasn't worth the iTunes crap to me and removed both.  Never used quicktime again since that day.

I've made careful, conscious, decisions around DRM purchases, file management and hardware purchases to avoid vendor lock-in as much as possible.  Much of my extended family is locked into iTunes due to different purchase decisions. I suppose if I had $2K in music, TV and movies from Apple, I'd be trapped too.

OTOH, I refuse to allow a Blu-Ray player in our house over the DRM issue and Ultra-Violet can forget it. I'm hated by the kids and spouse over that, but it has saved $$$$ and taught them about corporate DRM abuse. They've also learned about it when the Roku refuses to play movies when connected to our sound system thanks to broken HDCP.  I was really shocked when the Roku added HDCP to NASA - which does NOT require it.  Rentals, I don't have any issue with - it is the "purchase" of BluRay/Ultraviolet that bothers me. If they cannot 100% guarantee it will always playback on my current and future devices, AND can be willed to my kids, then grandkids all the way down the line - I don't want it.

Remember the MSFT "Plays for Sure" that only played on specific devices for 2-3 yrs? I do - not because I own any of that dead DRM, thankfully.  All the DRM since Apple/Blu-ray have been broken by design, IMHO.  Don't get me started about HDCP.

---

### Post by 1clue on 2015-05-06
Virtualization speed:  
I use virtualization pretty heavily both personally and through my work.  The only Windows VMs I have are through work.  Work is ESXi and Mac Parallels for host software, home is kvm.  One thing is universal:  Speed never sucks unless you have something starved for resources.  That said, I don't use audio or video through these machines, I can play video but there is no reason to, I can play audio but again there is no reason to.  I have no observations about speed*** [Edit: **about speed of audio/video with virtualization**]***.

It seems to me and everyone else I work with that putting a bunch of VMs on good hardware gets more performance than the hardware itself with just one of those operating systems.  Obviously there is a bit of overhead, but in real world experience all the guests are never under heavy load at the same time.  Usually one or two guests see heavy load.

Also I need to say that my Mac laptop (for work) has 8g RAM and can run 2 VMs without too much trouble, as long as nothing crazy is going on on the main system.  My 8g 2-core mac is being replaced by a 24g i7 linux box.  Today I would not consider buying a system which did not allow at least 16g for virtualization purposes. My latest purchase was an 8-core with up to 64g.

DRM:  
Generally speaking my only complaint about DRM is that I only want to do what normal people do -- watch the blu-ray, listen to the music.  I don't share it.  I'm irritated by the inability to play Blu-Ray on Linux.  I'm even more irritated by the fact that any time you see discussions about video playback on Linux, it is inevitably a discussion about breaking encryption and storing the movie on a hard drive, allowing playback in any room in the house.  And possibly in a lot of other houses.  It's talk like that which cause the movie industry to fear Linux.

Music:
All my music was purchased on CDs, and I still have them in a stack of boxes in the basement.  I've pulled that music into my Mac via iTunes, and have since transferred that to my sgn4 phone.  I generally don't have trouble with DRM for music, but I have an annoying duplication of songs every time I try to sync my phone on Linux.  I have yet to  figure out how to fix this.

---

