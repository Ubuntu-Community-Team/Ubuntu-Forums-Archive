---
title: "VMWare &amp; VitualBox same machine (+ other questions)"
date: 2011-06-13
forum: Virtualisation
---

### Post by SoFl W on 2011-06-13
I am slowly reading through the sticky pages listed above but I have questions I have not noticed answered.
I have used VMware in the past on Windows machines.  I currently have VirtualBox installed on this machine with several virtual machines installed. Several people on here suggested VirtualBox over VMWare, but there are also pluses for VMWare. 

I don't see why not but can I have both VMware and Virtualbox installed at the same time? There are no conflicting libraries or anything that would cause problems.

Can they be run at the same time? I would like to do side by side comparison.
 
If I export a machine in VirtualBox can I import it into VMWare?   I have a few machines I don't want to have to start over with, especially my Virtual Windows machine.  

-Thank you

EDIT:
I have a Virtual Windows machine, how does the virtual drive get fragmented?
EDIT2:  I think I just figured out this answer, but I will wait for a response to see if I am correct.

---

### Post by cwmoser on 2011-06-14
I have both VMware Player and Virtual Box on my 64-bit edition of Ubuntu Linux 10.04.  Both work great but like most folks I prefer Virtual Box.

Here are some of my observed Pros/Cons:

- vmWare VM's are portable to a Windows Host machine
- VirtualBox VM's run faster, boots up faster
- vmWare interferes with Open Office - causes it to freeze, not so with Virtual Box.

You can use GParted to resize the virtual drive for both types of VMs

I have not been able to convert a vmWare VM to VirtualBox - it just does not work for me.  I started with vmWare then started using VirtualBox and recreated my VMs in VirtualBox.

Carl

---

### Post by SoFl W on 2011-06-14
Thank you for your input.

---

### Post by jerrrys on 2011-06-14
also tried both and ended up with VB.  A big deal to me; can't take a snapshot with VM.

---

