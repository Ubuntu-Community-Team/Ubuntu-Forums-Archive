---
title: "VMWare Server Suddenly Running slow"
date: 2008-09-25
forum: Virtualisation
---

### Post by mespinos on 2008-09-25
I installed XP as a guest on Ubuntu 8.04 via VMware Server following the guide on the forums.  Everything ran beautifully and fast.  The boot time almost matched XP running natively.  
Recently my XP virtualization has been running like crap.  Ubuntu seems to still be fast, but it takes 5-10+ minutes to start up XP.  Once I get it loaded, everything lags really bad.

I have 4GB of RAM and I am runnin Ubuntu 64bit.
I have 2gb of ram assigned to XP and 2 CPUs.
I am running a dual core CPU.


Any thoughts? thanks

---

### Post by fjgaude on 2008-09-25
Have you used the disk defragger in Windows to defrag the VM space? Then after that do a Snapshot.

I'm assuming you have adequate disk space to not be swapping or having RAM swap.

---

### Post by mespinos on 2008-09-26
I will try both of those today with an update, thank you for the response.

---

### Post by mespinos on 2008-09-26
It seems to be back to normal speeds now, thanks.

---

### Post by fjgaude on 2008-09-26
Happy to see things are working correctly now...

---

### Post by veloce on 2008-09-27
> **mespinos said:**
> 
I have 2gb of ram assigned to XP and 2 CPUs.


I've had a lot of trouble with assigning the XP 2 cpus.  On some tasks, the vm will stall both processors.  I've found that Ubuntu's smp manages the various tasks from vmware better when the vms are set up as single core.

On a twin dual core server (i.e. four cores), the dual core vm performed no quicker than a single core.

---

### Post by fjgaude on 2008-09-27
That's right, VMs don't work well with the versions of VMware we are using... only one core should be used, period.

I think this "bug" is likely fixed in version 2.0 of VMware but not sure. My speed is good enough with only one core as to not be anxious about 2.0.

Just in:

[http://ubuntuforums.org/showthread.php?t=929780](http://ubuntuforums.org/showthread.php?t=929780)

Seems like 2.0 fixes the multi-core issue. Let's hope so.

---

### Post by mespinos on 2008-09-27
I hope so, I don't want to setup a new installation of XP.  You can change the processors assigned, but it recommends against it- 
Anyone done this?

---

### Post by fjgaude on 2008-09-27
Well, in 1.0.4 I started with two cores... then changed to just one, and everything has be fast ever since, going over to 1.0.7. I'm going to try 2.0 soon. I have it downloaded but everything is working so well now I linger...

---

### Post by mespinos on 2008-09-29
I have 2.0 running decently with 2 CPUs, should I change it to 1 core?  I don't wanna lose anything on the VM.

---

### Post by fjgaude on 2008-09-29
You will not lose anything by changing the number of cores.

If it is actly smart and quick then leave it where it is with two cores.

---

