---
title: "Dummy Question - Sorry  (Dual Booting)"
date: 2016-03-12
forum: Virtualisation
---

### Post by Quarkrad on 2016-03-12
Apologies for dummy question.  I am running 14.04 host and using VB 5.0.16.  I have a 12.04 guest and would like to experiment a few things with dual booting 12.04 and 14.04 within the VM - if it is possible.  So ... if I haven't explained myself properly.  I would like a dual booting (12.04 and 14.04) VM - so when I start the VM I get a grub screen offering me to boot to either 12.04 or 14.04.   I'm not sure how/if it is possible, once in my 12.04 VM  to boot to a 14.04 CD to install the 2nd OS.  Can this be done?

---

### Post by Quarkrad on 2016-03-12
This help me solve this:  [https://www.youtube.com/watch?v=b7UAVYMEY6w](https://www.youtube.com/watch?v=b7UAVYMEY6w)

---

### Post by MAFoElffen on 2016-03-12
install as if you would on a real mbr system. Partition your disks. You can create Multiple VM disks, assigned to one VM, to simplify your installation. Setup/install Windows OS first. Then your Linux System.

EDIT-- The reason I mentioned 2 VM disks... Is that if that "Windows Updates" just started having a challenge (on some systems) if grub is installed on the same disk as your Windows install and an Upgrade from a previous version of Windows to Windows 10 has problems dealing with extended logical partitions. These two issues are solved if you put your Linux Install (with Grub) on it's own disk ... and when you do "Windows Updates" change the boot order to the Windows disk. (Windows keeps thinking and believes that they should be the only OS that matters.)

---

