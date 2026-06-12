---
title: "KVM Virtualization Support in Feisty"
date: 2007-01-12
forum: The Cafe
---

### Post by aay on 2007-01-12
Now that [[COLOR="Blue"]Herd2[/COLOR]]("http://www.ubuntu.com/testing/herd2") has been released and Feisty has KVM support built into the 2.6.20 kernel.  I'm interested to hear how easy it will be to create set up and run.

I came across [[COLOR="Blue"]this link[/COLOR]]("http://www.metacafe.com/watch/358173/windows_xp_virtual_machine_on_linux_kvm/") which shows Windows XP running in KVM on Fedora Core 6 on a MacMini.  Based solely upon click responsiveness, I was surprised to see how fast this looks.  Again, my interest is in seeing how easy this will be to set up.  No doubt Xen would have better performance, but Xen hasn't made it into the mainline kernel yet and who knows when it will.

Anyone with any feedback/info on KVM in ubuntu?

---

### Post by ~LoKe on 2007-01-12
I don't know what this means.

Is it just better support for Virtual Machines, like VMWare?

---

### Post by G Morgan on 2007-01-12
KVM is as easy to use as Qemu is since it uses Qemu as its front end.

---

### Post by G Morgan on 2007-01-12
> **~LoKe said:**
> I don't know what this means.

Is it just better support for Virtual Machines, like VMWare?


KVM provides hardware virtualisation which the free VMWare products do not. It will only run on a system with the appropriate extensions in the CPU (hence hardware virtualisation) like Intel VT.

---

### Post by aay on 2007-01-12
> **~LoKe said:**
> I don't know what this means.

Is it just better support for Virtual Machines, like VMWare?

No.  KVM is it's own form of virtualization: [http://kvm.sourceforge.net/](http://kvm.sourceforge.net/)

---

### Post by ~LoKe on 2007-01-12
> **G Morgan said:**
> KVM provides hardware virtualisation which the free VMWare products do not. It will only run on a system with the appropriate extensions in the CPU (hence hardware virtualisation) like Intel VT.

I don't know what this Intel VT business is, but I've got a Core 2 Duo, would that be enough?

---

### Post by aay on 2007-01-12
> **~LoKe said:**
> I don't know what this Intel VT business is, but I've got a Core 2 Duo, would that be enough?

The guy in the video I linked to is running a Core Duo 1.66 on a MacMini which must support VT.  I think that means that all Core 2 Duos would support VT.  Am I mistaken on that?

Adam

---

### Post by ~LoKe on 2007-01-12
> **aay said:**
> The guy in the video I linked to is running a Core Duo 1.66 on a MacMini which must support VT.  I think that means that all Core 2 Duos would support VT.  Am I mistaken on that?

Adam

[http://www.intel.com/products/processor_number/chart/core2duo.htm](http://www.intel.com/products/processor_number/chart/core2duo.htm)
> Intel®
VT±
Looks like I'm in luck.

---

### Post by aay on 2007-01-12
> **~LoKe said:**
> [http://www.intel.com/products/processor_number/chart/core2duo.htm](http://www.intel.com/products/processor_number/chart/core2duo.htm)

Looks like I'm in luck.

Nice.  I've got a new System76 laptop on the way with a 2.0 GHz Core 2 Duo in it so it looks like I'm in luck too.

BTW, here's the Wikipedia page on KVM: [http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine](http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine)

---

### Post by ~LoKe on 2007-01-12
When they say the KVM has private hardware, does that mean that you'll need a second graphics card just for the VM?  Or does it just "borrow" from the current card?

---

### Post by G Morgan on 2007-01-12
> **~LoKe said:**
> I don't know what this Intel VT business is, but I've got a Core 2 Duo, would that be enough?

The 1.66Ghz T5500 does not have VT. The rest do I think.

---

### Post by mips on 2007-01-12
For those interested the new Sabayon comes with KVM installed by default.

---

### Post by aay on 2007-01-12
> **~LoKe said:**
> When they say the KVM has private hardware, does that mean that you'll need a second graphics card just for the VM?  Or does it just "borrow" from the current card?

I believe the only hardware prerequisite is a properly supported CPU.  Everything else is virtualized.

Adam

---

### Post by scoot1212 on 2007-01-18
I do believe you also need a bios that allows you to enable VT, not just a processor that support VT.

Scott

---

### Post by darkhatter on 2007-01-18
I have a AMD Turion 64 X2 and I got it too work (using edgy). I installed Windows XP and it ran amazing. I'm going to try out Mac OS X next and see how that works out.

by the way here is a tut. on how to install it in edgy:

[http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386](http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386)

---

