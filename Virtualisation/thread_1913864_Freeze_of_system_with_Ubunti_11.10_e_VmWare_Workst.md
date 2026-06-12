---
title: "Freeze of system with Ubunti 11.10 e VmWare Workstation"
date: 2012-01-23
forum: Virtualisation
---

### Post by rafanto on 2012-01-23
Since switching to Ubuntu 11.10 x86_64 (workstation) & Ubuntu 11.10 x86 (laptop) am having a lot of system freezes (gnome shell & Unity) when I use vmware workstation with various VM. I also have a lot of RAM (8gb) and I have no problems on the ram memory of it hardisk (I tested all components). During normal use the software if I switch from one window to another often hangs around.

To resolve this problem every time I reboot my machine, I would like to know if anyone has the same problem!? In addition, about which log files can I check what the problem is or what it does occur. And 'an urgent problem and annoying because I work on this machine.

thks

---

### Post by xterceptor on 2012-02-23
Hi!

oh dear.
I have exactly the same problem. Ubuntu 11.10. When i switch betweeen Host and Guest, often the complete system freezes and i have to reboot my pc.
I have no idea what i can do?!

greetz
xterceptor

---

### Post by nothingspecial on 2012-02-24
*Thread moved to **Virtualization**.*

---

### Post by dcstar on 2012-02-25
> **rafanto said:**
> Since switching to Ubuntu 11.10 x86_64 (workstation) & Ubuntu 11.10 x86 (laptop) am having a lot of system freezes (gnome shell & Unity) when I use vmware workstation with various VM. I also have a lot of RAM (8gb) and I have no problems on the ram memory of it hardisk (I tested all components). During normal use the software if I switch from one window to another often hangs around.

To resolve this problem every time I reboot my machine, I would like to know if anyone has the same problem!? In addition, about which log files can I check what the problem is or what it does occur. And 'an urgent problem and annoying because I work on this machine.


Have you updated your VMware to a 11.10 compatible version?

---

### Post by stn21 on 2012-02-25
The reason could be one of your memory-modules.

System Freezes (with any software including VMWare) can happen if one of the memory-chips has a problem. A problem like that can go unnoticed as long as no memory-hungry software is loaded. But when you load for example VMWare lots more memory gets used and then some arbitrary action like switching between vm and guest could trigger the actual freeze.

You have 8gb. I suggest to temporarily take out part of the memory modules. Try running your system with one 4gb-set of RAMs, then with the other set and each time see if it freezes. Load the VM each time and do some switching.

You could also run a memory-test, for example from ubuntu-live or the bootmenu. You have to leave that running for several hours to be sure. Hint: taking out memory-modules is a little more work but also is much faster than the memory-test ;)

---

### Post by Ficio on 2012-02-28
Hi,  I'm experiencing similar problems as well. Ubuntu 11.10 Desktop 64 bit, VMware workstation 8.0, recent update to 8.0.2 did not help. 16 GB RAM. I think it is Gnome Shell who freezes, as I'm able to switch to console (CTRL+ALT+F1) login, kill gnome shell process - this brings ubuntu back to login screen (and I'm avoiding hard reboot this way). No other stability issues, so I'm pretty much convinced it's not memory.  Can't connect this to switching back and forth between host/guest - however I have been always using guest console embeeded within Workstation window. Will try with RDP/VNC.  Haven't really experimented with other settings (read nVidia driver), but it is quite repeatable (and annoying as well).  Tyle Ficio

---

