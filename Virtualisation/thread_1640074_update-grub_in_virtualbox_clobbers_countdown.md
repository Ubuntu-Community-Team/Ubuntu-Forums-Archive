---
title: "update-grub in virtualbox clobbers countdown"
date: 2010-12-07
forum: Virtualisation
---

### Post by robertbub on 2010-12-07
For some reason, when unattended-upgrades runs update-grub within my virtualbox session (Ubuntu is the guest/client in this case), the count-down counter in grub no longer works -- it just sits there without any counter.

I'm using a VMDK file which maps to physical partitions, and my grub boot is installed on a partition, not on the MBR.  (And, in fact, the virtual machine doesn't have access to the entire hard drive (the one with the MBR record) or any of the other partitions (Windows, in this case).)

Does anyone have any ideas to fix it?  It's sorta annoying because I was hoping that my machine would auto-boot via dual-boot into Ubuntu when Windows [at its whim] decides to reboot itself.

---

### Post by CharlesA on 2010-12-07
So you installed Ubuntu to a partition on the hard drive by using VirtualBox?

If you wanted to dualboot, why not just do a dualboot normally, instead of messing around with VirtualBox inside Windows?

---

### Post by drs305 on 2010-12-07
Does the VM refuse to autoboot repeatedly or only the first time after a Grub update? 

If it's a one-time issue, when Grub finds an anomaly it will force a manual selection on the next boot. I don't know the cause but my solution if such is the case in a VM would be to just turn off updates to the grub-pc/grub-common packages by locking them in APT and Synaptic.

---

