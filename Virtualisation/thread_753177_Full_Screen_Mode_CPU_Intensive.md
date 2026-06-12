---
title: "Full Screen Mode CPU Intensive"
date: 2008-04-12
forum: Virtualisation
---

### Post by bluewhale on 2008-04-12
I'm running VMWare Workstation 6.0.2 on Ubuntu 7.10. I've just noticed that when I put the XP Pro client into full screen mode the CPU history shown in System Monitor goes nuts. All tracked 'cpu's' bouncing between 0 and 100 %, Very artistic, but ....??

As soon as I put it back into large window mode the CPU utilization goes back to normal. It isn't a burden as I can blow the window up to near full screen mode. 

But why would it behave this way?

---

### Post by fjgaude on 2008-04-12
Are you using more than one core of the CPU?

---

### Post by bluewhale on 2008-04-12
> Are you using more than one core of the CPU?

Yes. Both XP Pro when it was the only OS on this and now Ubuntu show 8 cores: 2 dual core Xeon's with hyperthreading enabled. My plan/goal is to use VMWare to tie a specific client OS to a particular physical core. More googling to do first tho. :biggrin:

---

### Post by fjgaude on 2008-04-12
From much of our experience, vmware really only likes one core... it's a bug that will hopefully be fixed in the next revision.

---

### Post by bluewhale on 2008-04-12
>  vmware really only likes one core

VMWare itself? Or are you referring to the client OS? 

If VMWare itself I'm pretty sure the ESX version loves multi-core rigs. But no matter: I'm just curious what changes in the relationship between VMWare Workstation and Ubuntu 7.10 when I change the client to full screen. The difference is dramatic. 

Thanks for the feedback.

---

### Post by fjgaude on 2008-04-12
The VM itself, Windows VM, can handle only one core... with more than one the VM has nothing but lags, slowdows, caused by "waits" for all cores to be free before it can access one.

The hypervisor likes multicore, the more the better.

---

