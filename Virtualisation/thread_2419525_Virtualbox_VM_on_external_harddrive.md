---
title: "Virtualbox VM on external harddrive"
date: 2019-05-23
forum: Virtualisation
---

### Post by hamburgerjungejr on 2019-05-23
Hi,

I have two harddrives in my Laptop. One permanently with the OS and one with an adaptor in the CD-Multi-Use tray.

To save space on my internal harddrive I chose the external harddrive as location for some of my VMs. 

Everytime I start Virtualbox the VMs on the external harddrive are marked as "not accessable". 
The machine shows the following error
```
  Runtime error opening '/media/****/ext*****/VM/V-ne****/V-ne****.vbox' for reading: -102 (File not found.).

 /build/virtualbox-NLghmB/virtualbox-6.0.6-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[750] (nsresult Machine::i_registeredInit()).


```

If I enter my harddrive in Nemo I cann access the VM. 

Is it possible to change this so that I dont need to access my harddrive through Nemo before using the VM?

---

### Post by TheFu on 2019-05-23
Yes.  Mount the partitions you need in /etc/fstab.

BTW, I wouldn't use /media/ for the mount point and hopefully, the file system is a Linux-based one. It is likely that the performance of the VMs will drastically improve, since gvfs mounts are usually slower than "real mounts."

---

### Post by hamburgerjungejr on 2019-05-23
The mountpoint was choosen by the system. I did not specify any mount path for this harddrive.

Both Harddrives are BTRFS.

I will try to add the mount to fstab

---

### Post by TheFu on 2019-05-23
I can't speak for virtualbox, but there was a warning against using btrfs storage for KVM VMs. [https://serverfault.com/questions/857024/linux-kvm-client-filesystem-btrfs](https://serverfault.com/questions/857024/linux-kvm-client-filesystem-btrfs)  Redhat has deprecated btrfs support.

/media/ is where gvfs mounts go. They are specifically for removable storage. According to the file system hierarchy standards:
> /media/
    Mount points for removable media such as CD-ROMs (appeared in FHS-2.3) 
[https://wiki.debian.org/FilesystemHierarchyStandard](https://wiki.debian.org/FilesystemHierarchyStandard)
Following the standards is the smart play.

---

### Post by hamburgerjungejr on 2019-05-24
> **TheFu said:**
> I can't speak for virtualbox, but there was a warning against using btrfs storage for KVM VMs. [https://serverfault.com/questions/857024/linux-kvm-client-filesystem-btrfs](https://serverfault.com/questions/857024/linux-kvm-client-filesystem-btrfs)  Redhat has deprecated btrfs support.

/media/ is where gvfs mounts go. They are specifically for removable storage. According to the file system hierarchy standards:

[https://wiki.debian.org/FilesystemHierarchyStandard](https://wiki.debian.org/FilesystemHierarchyStandard)
Following the standards is the smart play.

The harddrive is removable.
The slot for the CD-Drive is for multiple purposes. I can insert a CD-Drive, a harddrive tray or a second battery. So /media seems to be appropriate.
Until now I didn't noticed any problems using VirtualBox on Btrfs.


Adding the harddrive to fstab worked. Thanks!!

---

