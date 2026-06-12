---
title: "KVM for Dummies?"
date: 2010-11-30
forum: Virtualisation
---

### Post by reiki on 2010-11-30
Ok I'm really not a dummy, I promise, but for the moment I feel like one.

I use VMs for various purposes. Ubuntu 10.04 64-bit is my daily OS. I have VMs for XP, Win7 and OS X Snow Leopard. (I don't use the OS X much at all).

I started out using VMWare and have moved to VirtualBox. Lately I'm looking at KVM and trying to figure out if there is a reason to change from what I'm doing. The information I find seems to be a mix of old and new information so it's a bit difficult to determine what information is current and would apply to me. 

I would try simply installing KVM, but I've read that installing KVM disables other virtualization (like VirtualBox). 

Can someone give me a box of clues? Shed some light on this? Point me toward whatever is considered to be the most up-to-date information?

And does KVM really disable other virtualization? And if so, how hard is it to remove KVM if necessary so I can just go back to using VirtualBox?

---

### Post by gdahlm on 2010-11-30
The issue with multiple hardware accelerated hypervisiors is not just limited to KVM.  The issue is with how the VT extensions are implemented in the CPU, it is unsafe to have two hypervisors running at the same time.

That being said, if software virtualization performance is acceptable for your need you can run both at the same time or one or the other as hardware assisted virtualisation if the other is not trying to use it.

Documentation is sparse and confusing at the moment, it is a very fast moving target.

I would stick to [http://libvirt.org](http://libvirt.org) for information right now.

---

