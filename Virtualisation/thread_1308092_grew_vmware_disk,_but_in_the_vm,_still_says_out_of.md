---
title: "grew vmware disk, but in the vm, still says out of space"
date: 2009-10-31
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-31
so what else do i need to do? this vm is in one file.

scott@scott-desktop:/var/lib/vmware/Virtual Machines/xpprodell$ sudo vmware-vdiskmanager -x 15GB xpprodell.vmdk
  Grow: 100% done.
Disk expansion completed successfully.

WARNING: If the virtual disk is partitioned, you must use a third-party
         utility in the virtual machine to expand the size of the
         partitions. For more information, see:
         [http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1647](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1647)
scott@scott-desktop:/var/lib/vmware/Virtual Machines/xpprodell$

oh, i need to expand my windows partition, does anyone know of a tool to do ths in a vm?

---

### Post by fjgaude on 2009-10-31
From what little I know you have to use a Windows-based program to expand the VM size, like Partition Manager... good luck.

---

### Post by sdowney717 on 2009-10-31
got it using gparted livecd iso.

download gparted iso file and copy it into vm datastore
reconfigure vm machine cdrom to use an iso instead of physical drive
click the configure vm button on right
goto power tab
tell it to boot the bios
in bios reorder the boot so it boots cd drive first
boot up vm
it boots gparted
increase the partition size, not easy, for some reason mouse was not coordinating with xscreen, so mostly had to use keyboard.

it worked. but the mouse issue was awful pain

---

