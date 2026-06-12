---
title: "Virtualization of physical hardware"
date: 2018-05-16
forum: Virtualisation
---

### Post by Superdude_123 on 2018-05-16
I need some inspirational help to get started. I'm working on a project where after trying many different things, it seems that a licence to some expensive software (Windows XP system in a business environment, can't switch without spending lots of money) is assigned to the old PC's hardware. What I'd like to do is to create a virtual machine that on the software level emulates/virtualizes nearly all the physical hardware on the machine, and the rest of the stuff, I'll look in to doing pass through via the bios to the VM (I'll order a new PC if the recycled PCs here won't do it). 

Is there any good tools to get me started? Is VMware the only option available?

---

### Post by howefield on 2018-05-16
Thread moved to the "*Virtualisation*" forum for the moment, as it seems to be more suited to your question.

---

### Post by QIII on 2018-05-16
Hello!

Kernel-based Virtual Machine (KVM) is another technology available.  It is part of the Linux kernel, so costs nothing.  I run up to 17 machines at a time in KVM (that's all the free NIC ports I have together on the two machines I do this with) to emulate small slices of my clients' networks to simulate issues or test admin processes.  It doesn't cost me a dime for the virtualization.

What you are trying to accomplish can be done, but your first -- and least legally questionable -- route is to call the vendor and plead (grovel if need be) with them to allow you to reactivate on a new machine.  That would make things much easier.

Try that first.

---

### Post by Superdude_123 on 2018-05-16
Hey QIII,

That's my first step forward, but our fear is that as we go through some physical Windows XP machines that have been retired, we will eventually run out, so the virtualization seems to be our best "future proof" idea that keeps us going at the lowest risk.

Could the Kernel based VM emulate all physical aspects of a PC? Our best guess on how things are locked down by the vendor is that they must be using a serial number or generating a hash of the machine, so if we could "fake" the hardware, the disk image that we made would work.

We did try moving a clone of the machine to a new host computer and forcing XP to boot from the new hardware (still needs to be activated, but that's a future problem), but this did prove to be not successful as it would just not work.

---

### Post by QIII on 2018-05-16
Again, yes.  It can be done.  The legality is a grey area, which is why I suggested that your first step should be calling the vendor.  Explain the situation.  They may be merciful.

Unfortunately you can't call Microsoft about vendor-installed systems.  I have found Microsoft to be very helpful and quite understanding when I have needed to activate on a different machine when I went past my limit of re-installs (only one machine at a time) from the same disk.

You may need to carefully consider your ROI in terms of both the cost of the purchase of the equipment required to run VMs and the risk of the old and vulnerable operating system you want to install.  Compared to the cost of the purchase of the hardware, you may find that the software is only a fraction.  Using a currently supported version of Windows would also be a better bet for future-proofing than limping along with unsupported software that leaves you vulnerable to catastrophic risk.

Over the course of time, three (or whatever) copies of installation media and a machine capable of running three (or whatever) VMs may provide a greater ROI.

Your technical question can be answered.  The legal question is grey, which is why I hesitate.  Asking your vendor about allowing re-install on a new machine is iffy, but would solve your headaches with much less effort and, as a side benefit, would avoid possible legal issues.

---

### Post by LHammonds on 2018-05-16
I've converted quite a few physical machines to virtuals in the past but they were all done using VMware and the resultant VM HAL changed...thus the fingerprint of the system.

Best thing you can do is just try and see if it works.  If it doesn't, contact the vendor to see if they will let you migrate P2V.  Many vendors hate the idea because once it is on a VM, there isn't much to stop you from running multiple copies all over the place unless they support VMs and accounted for that during the design of the software.  If that do not support VMs yet, they might say "no" because their software (or the version you are running) isn't VM-aware...for licensing concerns.

Also, because the HAL changes, you will likely need to re-activate the OS as well.  If the hardware was using OEM version of Windows, you will have no choice but to buy another copy of Windows.

LHammonds

---

