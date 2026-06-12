---
title: "Server Virtualization Advice"
date: 2008-07-29
forum: Virtualisation
---

### Post by Viruk on 2008-07-29
Hi, 

I have been reading around about Virtualization and am now looking for some advice from someone who has done something similar. 

My current situation is that I am running several Ubuntu server setups (mainly LAMP stacks with services on top) on older desktop hardware. None of these run a GUI so I am not worried about gfx drivers or 3D support.

The current performance is fine - monitoring these servers with cacti shows that they rarely go above a few % CPU useage for long. I am hoping I can get quite a few guest OSs running on one server and use a second server as a backup in case of hardware failure on the first server.

We have recently replaced a couple of servers freeing up 2 dual Xeon servers for me to use so I'd like to virtualise many of the servers that are currently running. In case this makes a difference to any reccomendations, these servers have RAID5 SCSI arrays and are about 4 or 5 years old. (Also - will I need to use an SMP Kernel for the host to get the benefit of 2 CPUs? or is this support fairly standard in most hypervisors?)

Currently I am tending towards Xen or VMware, however I need to use free versions as I am in a school and the budgets don't stretch far enough to allow me to purchase any software this year. 

I have also read a bit about Ubuntu JEOS, but if I have it right this is more for the guest machine rather than a hypervisor layer. Currently I am planning to re-create my guest machines with JEOS to run on whatever hypervisor layer I choose. 

Ideally I would like to use a type 1 hypervisor (bare metal -> hypervisor -> guest OS) rather than a type 2 (bare metal -> OS -> hypervisor -> guest OS). 

Does anyone have any reccomendations for the hypervisor layer?

Can anyone post any links for guides/discussions about setting up the host system?

Thanks in advance for any input.

---

### Post by Fire_Chief on 2008-07-29
You may want to look into VMware's ESXi product as it was just released for free to download and use. The only real downside is you need to have a Windows system to manage it well through the Virtual Infrastructure Client application. This is the only Type 1 hypervisor I am aware of at the moment. Other hypervisors on the market run on top of an OS (Virtualbox, VMware server, Xen, etc.).

It is a straight install from a bootable CD (download ISO and burn). There may be some hardware compatibility limitations you should check before jumping in but other than that it should be a very solid product.

Cheers!

---

### Post by Viruk on 2008-08-01
Thanks for your reply Fire Chief, I spotted some information about ESXi but haven't had chance to do much readingh about that yet. 

I'll give it a try and see how it goes.

---

### Post by Viruk on 2008-08-01
I have also found Sun's xVM Server [http://openxvm.org/learn.html](http://openxvm.org/learn.html) so might have time to give that a try...

Does anyone have any experience of this?

---

### Post by PilotJLR on 2008-08-19
The Server xVM is still in beta, so you probably wouldn't want to use that quite yet...

I second the idea to use ESXi. If your hardware supports it, it is excellent.

---

### Post by HermanAB on 2008-08-20
My tuppence worth:
You mentioned that your servers are 4 to 5 years old.  You may find that the newer virtualizers like Xen, won't run on them.  VMware Server will however run on almost anything.

Cheers,

Herman

---

### Post by Viruk on 2008-08-27
Thanks for the extra replies - I haven't had time to revisit this yet, but I'm hoping to test some of these options soon =)

---

