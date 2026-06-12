---
title: "New &quot;Disk&quot; Inside Virtual Machine"
date: 2008-03-24
forum: Virtualisation
---

### Post by moogyd on 2008-03-24
Hi,

(I am not sure whether this is a Ubuntu or VMware question).

I am running Ubuntu 6.10 as a guest operating system (host Win XP) using VMware server 1.0.4.

I have created a new virtual disk (Hard Disk 2 : SCSI 0:1) in VMServer console. The question is, how do I access this disk from Ubuntu.

Any suggestions or pointers greatly apprecieated.

Thanks,

Steven

---

### Post by ruibernardo on 2008-03-24
If you already added the new disk to the VM, you have to partition it and format it to be able to use it. To do this use gparted that is in System > Partition Editor (if it isn't, install it with "sudo apt-get install gparted" or simply install the package "gparted" in Synaptic or whatever).

After creating the new partitions and mounting them, they should available to the system. Add the new filesystems to your /etc/fstab and change the options for auto-mounting, permissions, etc, as the other lines in it, but referring to the new partition(s).

** Warning**: be very careful with which disk and partitions you're messing with!

---

### Post by moogyd on 2008-03-24
Hi,

Thanks for the help. Managed to get it working.

Steven

---

