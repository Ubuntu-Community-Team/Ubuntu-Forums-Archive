---
title: "VMware server on Ubuntu server 12.04"
date: 2013-08-07
forum: Virtualisation
---

### Post by ernv84 on 2013-08-07
Hi guys,

I have been trying to find a thread on HOW TO INSTALL VMWARE SERVER ON UBUNTU. Gone thru some of the threads specially Virtualization mega thread but they all seems outdated.

Can someone please suggest how to install VMware server on Ubuntu 12.04. 

Would appreciate a quick response as i need to emulate Juniper routers for my exam. 

Thanks in advance

---

### Post by TheFu on 2013-08-07
VMware makes 6+ different tools for virtualization.  "Server" is beyond dead, beyond end of life. **nobody** - - --- NOBODY in the world should still be using it.  When I say nobody, I mean there is nobody anywhere in the world - nobody depending on this for life support, controlling nuclear reactors or anyone at home.  If any company is using it - they should have stopped in 2008 and moved forward.  Clear?

For server on server virtualization, check out:
* KVM
* Xen
* VMware ESXi

For Desktop on Desktop virtualization, check out:
* VirtualBox
* VMware Player
* VMware Workstation

For Server on Desktop virtualization, it gets fuzzy. In order:
* KVM
* Virtualbox
* VMware Player

The VMware tools can be fantastic, in a specific environment.  More and more, I avoid them - our company was screwed over by huge license cost changes. Since then, we've switched all our servers from ESXi to KVM.  We've also dumped Xen for KVM.

ESXi requires a Windows PC to manage. Cough - puke - nastiness. It is to be avoided.

So, hopefully, you'll reconsider the VMware Server idea.

---

### Post by ernv84 on 2013-08-07
Appreciate you efforts in explaining....i dont intend to use VMware for anything but Juniper Olive. I have tried that on GNS but it works horribly slow, tried Virtualbox no luck there either so hoping to crack it in VMware if i can. Still struggling though !!

---

### Post by Cheesemill on 2013-08-07
+1 for not using VMware Server.

Install VirtualBox and then follow these instructions...

[http://blog.poggs.com/2012/10/installing-an-olive-on-virtualbox/](http://blog.poggs.com/2012/10/installing-an-olive-on-virtualbox/)

---

### Post by TheFu on 2013-08-07
> **ernv84 said:**
> Appreciate you efforts in explaining....i dont intend to use VMware for anything but Juniper Olive. I have tried that on GNS but it works horribly slow, tried Virtualbox no luck there either so hoping to crack it in VMware if i can. Still struggling though !!

I found this [http://vmfaq.com/entry/55/](http://vmfaq.com/entry/55/) supported OS list.  8.04 was the last Ubuntu it worked with. I doubt it works on anything newer. Hypervisors are finicky.

As an alternative, is QEMU. [http://www.internetworkpro.org/wiki/Using_QEMU_with_Olive_to_emulate_Juniper_Routers](http://www.internetworkpro.org/wiki/Using_QEMU_with_Olive_to_emulate_Juniper_Routers) explains.  QEMU **is** supported on current Ubuntu releases. That how-to seems very straight forward to me.

Good luck!

---

