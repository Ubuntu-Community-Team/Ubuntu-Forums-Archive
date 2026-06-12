---
title: "Use from multiple OSes"
date: 2012-07-03
forum: Virtualisation
---

### Post by freakinjonathan on 2012-07-03
SETUP: COMPUTER With windows and linux host. 
EACH HOST HAS VIRTUALBOX.

Hey I have a dual boot setup of windows and ubuntu. On my windows partition is a .vdi file of Windows7. I can boot into that just fine. I made a snapshot.

Now my issue is that I boot into ubuntu, mounted my windows partition and added it straight into Virtualbox. I can boot it up just fine, but it's really weird. If I put a file on my desktop, then it will be there, when I come back on linux. But if I boot into Windows and start virtualbox, the file is no longer there. Same thing the other way. 

It like I'm using 2 seperate vms even though they both point the same vdi file.

---

### Post by sudodus on 2012-07-03
Do I understand correctly that you are using the same vdi file that is the same virtual drive? But you are using different virtual machines.

Are you saving the machine state (similar to hibernation) or shutting it down?

Could there be some disk caching, that is keeping the file to be really saved to the file system in the vdi file?

Maybe after backing up your [FONT="Courier New"].VirtualBox[/FONT] directory: What would happen if you use the same directory to save the machine states too (the [FONT="Courier New"]Machines[/FONT] subdirectory)?

---

