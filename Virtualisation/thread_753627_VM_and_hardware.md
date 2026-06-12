---
title: "VM and hardware"
date: 2008-04-12
forum: Virtualisation
---

### Post by ant2ne on 2008-04-12
Does a VMware Server OS know that hardware it is on? Can I move one VM from one machine to another without problems?

---

### Post by bluewhale on 2008-04-12
I'm new so take this with a grain of salt...

VMWare ESX is VERY picky about the hardware it's on,  due to the fact that it runs directly on the hardware. The Workstation and Free Server versions are not nearly as picky. From what I've read you GENERALLY can take any client and install it on another VMWare machine. 

This is because VMWare hides the actual hardware, offering it's own drivers and 'hardware' instead.  

But no, I haven't tried it yet. :biggrin:

I expect it will work, but I'm just beginning to catch my breath after moving my main work PC and my main home  PC to Ubuntu/VMWare a month ago. . There's a lot to like, but a small problem can be...... annoying.

---

### Post by fjgaude on 2008-04-12
I've moved the guest from machine to machine, even going from AMD to Intel without any troubles... with Windows you will have to register it again over the net if the hardware is real different, but that is all.

I've had this experience with VMware server, 1.0.3 to 1.0.5. Never had the opportunity to do it with other VM programs, like VBox.

---

### Post by PilotJLR on 2008-04-12
The only real hiccups from moving from intel / amd I've seen has been the with the virtual nic's, and that is really only with debian/ubuntu.
Your vnic mac address will change going from amd to intel, so you just need to edit (or delete) /etc/iftab. 
I had moved lightweight server vm's across platforms before. Since they were statically addressed, then I just commented out the mac address for eth0 in iftab, which enables the new vnic to take eth0.


What is really cool is that ESX / VC can move guests across hardware while they are still running! Of course, that is very picky on hardware and most certainly not free.

---

