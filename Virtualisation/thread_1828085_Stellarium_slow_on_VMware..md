---
title: "Stellarium slow on VMware."
date: 2011-08-18
forum: Virtualisation
---

### Post by jkdbuck76 on 2011-08-18
XP host machine.
 
Running latest VMware.
 
Using Ubuntu Natty Narwhal.
 
I've enabled 3-D graphics.
I'm running Ubuntu Classic desktop.
 
I've allocated 775megs to RAM since this machine only has 2.0G of RAM.
Processor is an Intel(R) Core(TM)2 Duo CPU
E7300 @ 2.66 GHz.
 
Any ideas?
 
I've tried downloading drivers, but it does not give me any drivers for the monitor.

---

### Post by Jake.Debord on 2011-08-18
What do you have set for video ram?

---

### Post by jkdbuck76 on 2011-08-18
> **Jake.Debord said:**
> What do you have set for video ram?
 
I do not know.  Is that on the host or guest machine?

---

### Post by Jake.Debord on 2011-08-19
> **jkdbuck76 said:**
> I do not know.  Is that on the host or guest machine?


I assume guest machine. If Stellarium is graphics intensive, and a google search says it probably is... then you need to make sure you give it enough video ram. Its like the graphics on your host machine gets its ram from your video card or on board, but your guest machine gets its vram from your settings.

---

### Post by TimmyK. on 2011-08-20
Although why don't you run Stellarium in Natty? It would run a lot nicer.

---

### Post by jkdbuck76 on 2011-08-23
> **TimmyK. said:**
> Although why don't you run Stellarium in Natty? It would run a lot nicer.
 
 
I am running Natty.

---

### Post by TimmyK. on 2011-08-24
I mean why bother running it inside a virtual machine when you can just install it from the software center and run it on the guest OS?

---

### Post by jkdbuck76 on 2011-08-24
> **TimmyK. said:**
> I mean why bother running it inside a virtual machine when you can just install it from the software center and run it on the guest OS?
 
I can run it on XP?

---

### Post by TimmyK. on 2011-08-24
Trust me, Stellarium always runs more nicely on Linux, and any programs always run better on the host machine. I'd say your best bet is installing it on Natty, not on virtual XP.

---

### Post by 73ckn797 on 2011-08-24
> **TimmyK. said:**
> Trust me, Stellarium always runs more nicely on Linux, and any programs always run better on the host machine. I'd say your best bet is installing it on Natty, not on virtual XP.
+1 on this comment.

---

### Post by dcstar on 2011-08-29
> **TimmyK. said:**
> Trust me, Stellarium always runs more nicely on Linux, and any programs always run better on the host machine.

Especially anything graphics intensive since most VM environments only provide "Second hand" 3D graphics emulation at best.

Only with proper Hypervisor platforms do VMs approach native hardware performance - people should install something like the (free) Vmware Esxi and then run all their hosts as VMs to see the difference.

---

### Post by jkdbuck76 on 2011-08-29
ok.  thanks, folks.

---

