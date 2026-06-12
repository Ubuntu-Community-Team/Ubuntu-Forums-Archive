---
title: "Virtual Box in Ubuntu 14.04"
date: 2016-02-21
forum: Virtualisation
---

### Post by jerry50 on 2016-02-21
I have a dual boot system:  win 7 and Ubuntu 14.04.  I'm playing around with virtual box on the linux side of the computer and I'm trying to just put another ubuntu 14.04 on virtual box.  I'm using Virtual Box that is listed in the Ubuntu Software Center.  I'm not sure if this is Oracle or not.  Anyway, after setting everything up, when I hit "start" I get this message:     Failed to open a session for the virtual machine Ubuntu 64 bit.  VT-x is disabled in the BIOS.   (VERR_VMX_MSR_VMXON_DISABLED).

What do I do?  Step by step.  I'm a noob.

---

### Post by howefield on 2016-02-21
Thread moved to the "*Virtualisation*" forum.

---

### Post by deadflowr on 2016-02-21
Well basically you will need to shutdown the machine.Then restart it and in the very first screen shown for the machine, click on the button the screen tells you open the bios section.
The bios section might also be called system or system settings or something to that affect.
(These button are usually something like F2 or some other F button; Usually, but not always, as I had one once that was the delete key.)

Then inside the bios system section, look around to find anything related to virtual machine or virtual machine extensions, or virtual extensions; best if it actually says vt -x (one can hope), and enable it.
Then before exiting, make sure to save the changes.

then boot like normal and the vt -x settings should be enabled allowing you to run virtual machines.

Hope it helps

---

### Post by MAFoElffen on 2016-02-21
+1 to that...

To be able to do that, the CPU needs to have have virtual hardware flags of vt-x for an Intel cpu or amd-v for an AMD cpu. 

You can check for those flags in the Ubuntu side of you your dual boot by:
```

cat /proc/cpuinfo

```
If you could post the results of that we could help you determine that... Also post the make/model of your PC, so we have an idea of your BIO.

If your cpu is cabable, then it also has to be enabled in the BIOS for it to be able to be enabled in a hypervisor such as VirtualBox (If not, that option will be grayed-out in VirtualBox).

If your cpu is not cable, that is not the end of the world... That just means that you would be limited to installing and running 32 bit OS'es.

---

### Post by jerry50 on 2016-02-21
Working like a charm.  Just went to BIOS and found the virtualization then enabled it, and voilà!  Thanks for everyone.

---

