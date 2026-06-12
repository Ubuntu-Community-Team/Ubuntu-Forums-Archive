---
title: "XEN on non VT-x CPU, is Kernel modified for Xen?"
date: 2009-04-06
forum: Virtualisation
---

### Post by UranUtan on 2009-04-06
Hi,

In this post I actually ask several independent questions about XEN. I would like to try out XEN. I have made a cursory reading of XEN Documentations and some howtos. But I am still confused, I hope some of you familiar with using XEN as Domain0 could give me some guidance.

Q1. I have an old Pentium 4 Prescott 2.8 GHz which is 64 bits, HT but is NOT VT-x compatible. Can I install the latest XEN version on this computer? If yes, can I run a Windows VM AND still continue to use my Ubuntu Desktop? May be this is a stupid scenario, but I would like to know if XEN can run as a host-based hypervisor like VirtualBox.

Q2. Now assuming that I have the proper hardware to run XEN. Documentation says that I can get XEN via the Synactic package manager. But should XEN require a modified kernel? If so would that mean that the computer will become totally dedicated to run the Xen hypervisor? I mean, once rebooted with Xen, the Ubuntu desktop I used to see will be gone? (all data, Gnome, Compiz, applications, etc?)

Q3. If I want to setup a dedicated Xen Server, it will be used to host from 4 to 8 Windows VMs. Guest OS are UNmodified Windows 2003, Vista, Win7, Win2008 (x32 and x64). These Windows VMs are used for dev testing, there is no need to have multimedia. What would you recommend as setup procedure.

I understand this is a vast question. I don't need a 50 pages installation procedure. I just need the important steps and I will try to read the doc further. For example, I know that the CPU must have VT capabilities. But for XEN itself, should I compile it from source, get it from Ubuntu repository? How to make a modified kernel? Or should I boot the XenServer ISO from Citrix? And to prepare the Windows VMs, is there a front end admin GUI or should I use command line?

Thanks very much in advance for any help.

---

### Post by juancarlospaco on 2009-04-07
Q1)Yes, you can install the latest XEN version on your computer, you CANT run windows since you dont have Virtual Extensions on your Microprocessor, to run windows you need Virtual Extensions.

Q2)XEN require a modified kernel if you DONT have Virtual Extensions, XEN is like a microkernel baremetal-friendly, but you dont loose all your data installing Xen.

Q3)You CANT, ...to run Windows you need Virtual Extensions, if not Linux Only Guests.


**[COLOR="Red"]XEN (from Xen.org) is NOT the same of XenServer (from Citrix.com)[/COLOR]**

XenServer have a Citrix free open source Admin console (comes on the XenServer .ISO too)
XenServer is Bare-Metal Only Hypervisor, 
no OS, no Ubuntu Host, no grub, only XenServer and the hardware, the installation format entire disk.

---

### Post by UranUtan on 2009-04-07
Hi Juan,

Thanks for your answer. Understood for the VT-x feature of the CPU to run Windows VM. What are the main differences between the Xen from xen.org ([http://www.xen.org/download/](http://www.xen.org/download/)) and Citrix XenServer ([http://www.citrix.com/lang/English/lp/lp_1688615.asp)?](http://www.citrix.com/lang/English/lp/lp_1688615.asp)?) 

I think this is the main cause of my confusion. Citrix XenServer is a bare metal solution like VMWare ESX. So then it needs a dedicated server, no OS. Simple, you boot from the CD and the entire machine is dedicated to XenServer.

But what is the XEN Server in the Ubuntu repository? is it a host based hypervisor? Because if it was "bare metal" (type Paravirtualization), I don't know how Ubuntu can co-exist with Xen as Xen should have a specifc kernel which strips out all the features not needed by the hypervisor. For example: Games, OpenOffice, Compiz, etc. these stuffs have nothing to do with a bare metal hypervisor.

So pratically, here a simple question: if you get XEN from Ubuntu repository. What would happen to your machine?

- Can you still use Ubuntu Desktop exactly like before Xen?

- If yes, then what can you do with Xen which is newly installed on top of the Ubuntu OS? Sorry I am confused, I don't see any value in this scenario, it is no better than a host based hypervisor like VirtualBox.

Sorry for silly questions, I should probably try out to see by myself. But I would appreciate if you can give some hints.

---

### Post by AlanP123 on 2009-04-07
Hi

I *think* (early investigations) the way it works is that with a CPU supporting virtualisation natively, you can use unmodified OSs like windoze.  With older CPUs, you may need to use paravirtualisation, which requires kernels modified to support same (and such kernels may be particularly efficient, as they use memory buffers instead of emulating hardware device I/O.)

VMWare have a bunch of patents that seem to refer to a heap of software tricks enabling support of unmodified OSs on non-virtual (older) CPUs, but that stuff is a) slower (involving emulation of individual instructions), and b) unnecessary on current hardware....

... I think.

---

### Post by UranUtan on 2009-04-10
Found the info in this blog. Xen modified the Linux kernel for itself and re-exposes another Linux guest so we still think we have the same machine than before Xen was installed.

> Xen is a hypervisor that is based on the Nemesis microkernel. Linux distributions ship Xen today and by default install a Linux guest (known as domain-0) and do their best to hide the fact that Xen is not a part of Linux. They've done a good job, most users won't even notice that they are running an entirely different Operating System.

Complete: article: The truth about KVM and Xen (Friday, May 09, 2008)
[http://blog.codemonkey.ws/2008/05/truth-about-kvm-and-xen.html](http://blog.codemonkey.ws/2008/05/truth-about-kvm-and-xen.html)

---

