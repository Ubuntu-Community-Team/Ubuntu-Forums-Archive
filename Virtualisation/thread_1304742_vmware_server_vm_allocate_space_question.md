---
title: "vmware server vm allocate space question"
date: 2009-10-29
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-29
i created an xp vm.
but the disk is slowing it down and even affects my ubuntu host. firefox on the host will go grey since it cant respond etc...
while the disk activity is engaged everything sort of stops.

I thought it was due to when i created the vm and told it to grow as needed.
so i ran the conversion to specify to a type 2 disk and increase it's space to a fixed size. the process ran thru and completed but the virtual machine still acts the same crappy way of tying up everything with long disk accesses. 
am i going to have to start over with a pre allocated space? it is really pretty bad running this way.
i have 4gb on a core2duo with a 250gb ide drive. 
i let the vm have 512mb since that was the default, should it be more??
I am going to switvh out the drive to a sata and it might help speed things up.

---

### Post by chrisling on 2009-11-10
Mine is the same with the firefox grayed out while having winxp running on vmware player, it is doing it every no and then, even when winxp is at sleep (screensaver's out).  

The winxp VM is a 20GB pre-allocated flat vdmk file, so this should rule out VM file partitioning doubt.

VMX settings: 1 CPU (Core2Duo T5500 1.6GHz), 512MB Ram, IDE0:20GB Sound, USB, CDROM.

---

