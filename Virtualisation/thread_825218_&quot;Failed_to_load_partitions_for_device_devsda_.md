---
title: "&quot;Failed to load partitions for device /dev/sda: Insufficient permission to access fil"
date: 2008-06-10
forum: Virtualisation
---

### Post by anystupidname on 2008-06-10
When running VMare as my user and attempting to select physical disk partitions, I get the error "Failed to load partitions for device /dev/sda: Insufficient permission to access file". I am running Vmware Workstation 6 (build 45731) on Kubuntu hardy. It is a dual boot machine and must remain a dual boot machine (windows xp).

Partitions are as follows on /dev/sda:

swap

/

XP

/other

I've confirmed my user is part of the "disk" group.

When running VMware are root, I don't have the same problems but I cannot continue to run VMware as root...

If I create it as root and change the permissions after, then it says it can't find the vmdk files when you try to start the vm...

Are there any logs that would help me here?


Please help! Any assistance would be much appreciated!

---

### Post by mkrate on 2008-06-11
Same problem here! Trying to switch to ubuntu, but depend on XP running through VMWare for now; the virtual machine needs to see my other hard drive. Any help very welcome!

---

### Post by anystupidname on 2008-06-11
Well, I upgraded feisty to hardy and vmware workstation from 6.0.0 to 6.0.4 and one of those things apparently fixed the problem...

---

