---
title: "Virtualize/how to use Windows graphics apps via Linux"
date: 2015-02-13
forum: Virtualisation
---

### Post by thenox on 2015-02-13
I know there's a lot of info here about virtualization. But I still haven't found a good solution, after having tried different things and read up quite a bit. 

I use a several resource-intensive 3D apps such as Lightwave, eon software's Vue Xtream, and Substance Designer (Allegorithmic). These are the only things that keep me in Windows. Otherwise I would switch over to Linux completely. 

I'm wondering how I could use these apps from within Linux (Ubuntu 14.10). 
   - Dual booting has been solution so far, but it's not a good one. B/c I have to switch back and forth b/w apps (say, running Lightwave or Blender, and jumping into Substance Designer to create or tweak high res textures), I end up mostly using Windows 7. 
   - I can run Maya in Linux, of course. I've used virtualbox to create a virt machine, installed Win 7. But these apps eat CPU and RAM. (Substance Designer especially, can eat all the RAM you have when dealing with complex node graphs and/or high rez textures.) So virtual machines are a catch22.
   -  Wine won't run any of these apps reliably


**Questions:**
  1. Is there a way to run virtual machine w/ no overhead? 

  2. Is there a service to run your apps in the cloud somewhere, and access them that way through Linux? 

Thank you in advance if you have a chance to respond.

---

### Post by SeijiSensei on 2015-02-13
Obviously you can't run virtual machines with literally "no overhead." There's the overhead of the host operating system.  VirtualBox itself is pretty lightweight though.  How much memory does your machine have?  I usually give Windows at least 3/4 of the system's memory whether it's the guest or the host.  On a 4-8 GB machine, I give Linux 1-2 GB.  If I owned a 16 GB or larger machine, I'd devote 2 GB to Linux, and leave the rest for Windows. 

I'd actually be more concerned about the video performance if Windows is running a VM since you have to make do with the virtualized video adapter.  Given the kinds of tasks you're describing, I'd make Windows the host OS and run Linux in a VirtualBox.

---

### Post by thenox on 2015-02-13
Thanks, SeijiSensei. 

I've read something about hardware virtualization, such as KVM. Would that be better than Virtualbox?

---

### Post by SeijiSensei on 2015-02-13
Others will have to answer that, as I have only used VirtualBox.  Still I don't see why you wouldn't be better off with Windows as the host OS and Linux as the guest.  If you run the Linux guest in full-screen mode, you'll forget there's a Windows installation underneath it until you need it.

---

### Post by thenox on 2015-02-13
Hmm, not a bad idea, I suppose. I've always thought that I should use Linux as the primary OS, but yeah, if it's in a Virtbox, fullscreen, that might be better. Good call.

---

### Post by MartyBuntu on 2015-02-13
> **SeijiSensei said:**
> If you run the Linux guest in full-screen mode, you'll forget there's a Windows installation underneath it until you need it.

...or until anti-virus does a scan or Windows Update kicks in and your machine slows to a crawl.

---

### Post by SeijiSensei on 2015-02-14
Anti-virus?  What's that?  My mail server runs [MailScanner](http://www.mailscanner.info) so I never get infected emails, and I'm experienced enough to spot junk that might be dangerous. Not that I read my mail in Windows, and rarely browse the web in Windows either.  99% of the time I'm using Linux.  Also you can schedule Windows Update to happen at off-hours like 3 am.

---

### Post by KillerKelvUK on 2015-02-14
I run Ubuntu 14.10 as my host and then a range of linux, windows and mac guests (not all at once)...I have an i7 with 16GB of ram but I don't use Windows for what you need it for as in my needs are less graphics/ram intensive.  If you have a read up on "VT-d and IOMMU" you can dedicate certain physical resources to a virtual machine with near native performance.  You'll find a lot of posts, especially in the Arch linux space where people do this for graphics cards to get top notice Win7 VM performance for gaming...if the considerations are similar for you i.e. you have dedicated PCI processing hardware then you can pass this through to your Win guest (caution here as this isn't beginners stuff!).

Giving a VM more CPU and RAM is simple provided you have the resources available in the host.

---

### Post by TheFu on 2015-02-15
> **SeijiSensei said:**
>  I'd make Windows the host OS and run Linux in a VirtualBox.

Exactly.  Plus all the other stuff seems reasonable **FOR THIS SPECIFIC WORKLOAD.**
RAM and Video intensive Windows applications.

For normal Windows stuff, give a VM 1 vCPU and 1.5G of RAM. This is enough for 7MC to record 2 HiDef TV shows concurrently. 

KVM is more for server-on-server needs, though some people use it for GPU passthru for Windows gaming.  This is expert-level stuff still and even then hit-or-miss.  Since I don't game, don't have 2 GPUs in any machines (required).

Sometimes the easy answer is a $30 [KVM-switch]("http://www.amazon.com/TRENDnet-2-Port-Switch-Cable-TK-209K/dp/B000L4D42Q/") and another machine.

---

### Post by thenox on 2015-02-16
> **MartyBuntu said:**
> ...or until anti-virus does a scan or Windows Update kicks in and your machine slows to a crawl.

Good to know. I'll have to keep an eye out for that.


> **KillerKelvUK said:**
> I run Ubuntu 14.10 as my host and then a range of linux, windows and mac guests (not all at once)...I have an i7 with 16GB of ram but I don't use Windows for what you need it for as in my needs are less graphics/ram intensive.  If you have a read up on "VT-d and IOMMU" you can dedicate certain physical resources to a virtual machine with near native performance.  You'll find a lot of posts, especially in the Arch linux space where people do this for graphics cards to get top notice Win7 VM performance for gaming...if the considerations are similar for you i.e. you have dedicated PCI processing hardware then you can pass this through to your Win guest (caution here as this isn't beginners stuff!).
Giving a VM more CPU and RAM is simple provided you have the resources available in the host.


Interesting. Getting native or almost-native performance from a VM would be awesome. Ideally, I'd like to use Linux as my main/host OS, if possible, though for starters I'll use a Win7 host, Linux guest.

Some of that is probably over my head, but I could try it. What exactly would be "dedicated PCI processing hardware?" As in an extra PCI graphics card? 


Thank you, all, for the replies and help.

---

### Post by TheFu on 2015-02-16
[http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175) 
 [https://wiki.debian.org/VGAPassthrough](https://wiki.debian.org/VGAPassthrough)

---

