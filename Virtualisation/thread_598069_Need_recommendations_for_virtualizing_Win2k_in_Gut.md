---
title: "Need recommendations for virtualizing Win2k in Gutsy 64 bit"
date: 2007-10-31
forum: Virtualisation
---

### Post by timzak on 2007-10-31
I've been using Feisty 32 bit on a 64 bit machine since April and dual-booting into Win2k specifically for Microsoft Money 2006 and backing up DVD movies.

I'm getting a bit tired of the dual-boot process and would like to experiment with virtualization.

I'd like to keep this as reliable, simple and tinker-free as possible.  I only need to run MS Money and DVD backup software.  No games, nothing else.

1) Are there any compatibility issues with MS Money 2006 and virtualization?
2) Are there any specific compatibility issues related to running Gutsy 64bit?
3) Can I backup DVDs through a virtual machine?
4) based on my needs above, what is the simplest virtualization package to use?

Thanking you in advance.

---

### Post by timzak on 2007-10-31
*bump*

---

### Post by AusIV4 on 2007-10-31
1)I know very little about MS money, but unless it uses 3d accelleration, there's no reason it shouldn't run in a virtual machine.
2) I don't use 64 bit, so I don't know.
3) I don't see why not, but there are DVD backup utilities for Linux, so unless there's something very specific, I see no reason to do that through a virtual machine.
4) I find VMWare Server to be the easiest to use, though I'm not sure about 64 bit packages. A lot of people here swear by Virtual Box, but I find VMWare to be more straightforward.

---

### Post by smohan1962 on 2007-11-08
I use Virtualbox on Gutsy. Works well. Only problem I saw was if Windows VM is running and you try to shutdown, dialog waits for confirmation. Post that, kbd based GUI navigation but not mouse.

I've installed WinXP, a stock tracking s/w, skype, yahoo messenger.

Mohan

---

### Post by EmmEff on 2007-11-08
> **timzak said:**
> 1) Are there any compatibility issues with MS Money 2006 and virtualization?

The only applications that have issues with virtualization are those that require advanced CPU and/or graphic card features (ie. 3D acceleration).  I've not used Money 2006 but I am a regular user of Money 2002 on XP running under VMware Server and VMware Fusion.

> 2) Are there any specific compatibility issues related to running Gutsy 64bit?

Related to?  I am typing this message on a Gutsy x86_64 installation running VMware Server with several 64-bit VMs running concurrently.

> 3) Can I backup DVDs through a virtual machine?

Yes, but performance many not be as good as running on physical hardware.

> 4) based on my needs above, what is the simplest virtualization package to use?

VMware Server is proprietary, but free to use.  There are also VirtualBox, KVM, and Xen OSS which will all run Windows at differing degrees of compatibility.  The latter group of virtualization platforms require Intel VT or AMD hardware virtualization support in the CPU to run non-paravirtualized OSes.

HTH

---

