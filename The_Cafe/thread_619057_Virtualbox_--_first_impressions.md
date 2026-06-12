---
title: "Virtualbox -- first impressions"
date: 2007-11-21
forum: The Cafe
---

### Post by toupeiro on 2007-11-21
So far, I am very impressed.  I've been a vmware guy for years, and actively support multiple Vmware ESX servers.  VirtualBox is a beautiful piece of software.  My first virtualbox VM is going to be a FreeBSD box.

I would like to see a bare metal implementation of this product, similar to ESX, which will allow dynamic allocation of resources across multiple virtual machines, and the ability to migrate guests across multiple hosts using shared storage Put that together, and there would be little reason to consider VMWare.  (I hate their licensing model!)

---

### Post by jespdj on 2007-11-21
I've also tried both VMWare and VirtualBox myself.

One thing that IMO is a major missing feature in VirtualBox is that it does not support multi-core processors well. I have a dual-core processor, but virtual machines inside VirtualBox see only one processor (one core). I want to use a virtualization tool to run Windows for when I occasionally need to use Photoshop CS3, but if VirtualBox lets Windows and Photoshop use only half of my processor... then that's a big limitation.

VMWare does support multi-core processors properly (you can choose how many cores/processors a VM should see).

---

### Post by toupeiro on 2007-11-21
> **jespdj said:**
> I've also tried both VMWare and VirtualBox myself.

One thing that IMO is a major missing feature in VirtualBox is that it does not support multi-core processors well. I have a dual-core processor, but virtual machines inside VirtualBox see only one processor (one core). I want to use a virtualization tool to run Windows for when I occasionally need to use Photoshop CS3, but if VirtualBox lets Windows and Photoshop use only half of my processor... then that's a big limitation.

VMWare does support multi-core processors properly (you can choose how many cores/processors a VM should see).

Well, you beat me to it :)  I hadn't even checked the options for SMP yet, because BSD is still installing and I need to power it down to get into those settings.  Yes, SMP is huge for me too as I have a multi-core system, and I've been watching how it behaves with my proc.

---

### Post by Dripbagulhos on 2007-11-21
Hello,

I had the same good impression about the new VirtualBox. I've donwloaded and installed the AMD64 version and enabled the AMD64 extensions. I don't know if it is the reason, but my Windows XP machine is significantly faster on Virtualbox than on VMWare. It also consumes less cpu and boot in less than 45 seconds.

Another point: in VMWare there is one key (on any keyboard I tested) that does not work : "/" and "?", the key that stays besides the right shift key. In Virtualbox it does work!

---

### Post by toupeiro on 2007-11-21
probably so.  Windows becomes an application, and even though its an os with 32-bit limitations, its running in a 64-bit environment, which means in a round-a-bout way, it is benefiting from the advantage of 64-bit block sizes versus 32-bit block sizes.  64-bit virtualbox should be able to push 32-bit windows a little better than 32-bit windows could push itself.  It's not getting the full advantage of a 64-bit host, but it should be receiving some.

---

