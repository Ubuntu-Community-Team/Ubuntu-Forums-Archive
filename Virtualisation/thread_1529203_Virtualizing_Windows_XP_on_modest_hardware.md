---
title: "Virtualizing Windows XP on modest hardware"
date: 2010-07-11
forum: Virtualisation
---

### Post by MetalheadGautham on 2010-07-11
Here is my system configuration:

Ubuntu 9.10 (soon upgrade to Ubuntu Studio 10.04)
Acer eMachines e725 Laptop
Intel Pentium Dual Core T4400 2.2GHz 1MB L2 Cache (No support for intel-vt)
1GB DDR2 667MHz RAM
Intel GMA 4500 Graphics

I need to install a copy of windows xp 32bit in this.

How comfortable will the system run, if I run low end windows games ?

most probably I will be allocating 512MB RAM to the virtual machine.

And which is the best virtual machine suited for my purpose ?

Does any virtual machine support allocating an entire physical processor core to it ?

---

### Post by Khakilang on 2010-07-12
I have try Virtual Box OSE on my computer which has a similar spec but mine is running at 1.8GHz and 1.5GB RAM. No problem running it but it could not recognize my USB port. Than I realize that the OSE doesn't support USB so I am trying other Virtualization like Virtual machine manager. So hope everything run smoothly. Will come back again to help or find help.

---

### Post by HermanAB on 2010-07-12
I have run WinXp in Virtualbox on a 400MHz EEE PC and it worked fine.

However, gaming on a VM is not recommended, due to graphics issues.

---

### Post by fjgaude on 2010-07-12
Try using VMware Player 3.1.0, allocating 512M memory to XP... will run just fine. One CPU core is all you need... try it and see.

---

### Post by MetalheadGautham on 2010-07-17
I just tried Virtual Box.

And after using it I found it to be highly buggy.

Its usage of right-ctrl key to shift focus doesn't work properly. It takes control of the keyboard and mouse and never returns them on pressing the right-ctrl key.

Which other virtual machine has nice implementations of OpenGL and/or DirectX along with other features for x86 PC emulation ?

---

### Post by fjgaude on 2010-07-17
Give VMware Player 3.1.0 a try... for most it is flawless!

---

### Post by TheFu on 2010-07-18
> **MetalheadGautham said:**
> I just tried Virtual Box.

And after using it I found it to be highly buggy.

Its usage of right-ctrl key to shift focus doesn't work properly. It takes control of the keyboard and mouse and never returns them on pressing the right-ctrl key.

Which other virtual machine has nice implementations of OpenGL and/or DirectX along with other features for x86 PC emulation ?

You can change the VirtualBox capture/de-capture keystokes. I use F12 myself.  Also, you can install the guest additions which handle capture/de-capture automatically based on the mouse location.

Just some more options for you.

---

### Post by Dedoimedo on 2010-07-19
I run virtualbox 3 in ubuntu lucid on t42 with single core, 1.5gb ram. XP runs as a virtual machine with 512mb ram from an external USB disk, works great. Placing the virtual machines on a second disk or external device will grant you a major performance boost.

Dedoimedo

---

