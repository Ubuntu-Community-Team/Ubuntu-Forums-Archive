---
title: "KVM and LVM Volume Group Storage Pools"
date: 2013-06-06
forum: Virtualisation
---

### Post by BostonDriver on 2013-06-06
I'm looking to better understand the relationship between KVM and how it uses LVM Volume Group (VG) for a storage pool.

How does the LVM Volume Group relate to the rest of the system?   Is the VG dedicated  to KVM?  Or can Logical Volumes (LV) be created on this VG via lvcreate allowing filesystems to be used?

Thanks for any info.

---

### Post by heiko_s on 2013-06-07
LVM has nothing to do with KVM and vice versa. LVM provides a logical volume manager, which allows you to organize your storage media (hard drives, SSD, etc.) in a more flexible way.

Both Xen and KVM can use RAW storage provided by LVM. In that case you just create a LV (Logical Volume) in a VG (volume group) without creating a file system. This will be done in the guest (VM). The kpartx command in Linux can be used to access those RAW file systems from without the guest OS.

Of course you can also create a file system in an LV, for example ext4 for Linux.

---

### Post by BostonDriver on 2013-06-08
> **heiko_s said:**
> LVM has nothing to do with KVM and vice versa. 

LVM Volume Group is a perfectly valid type of KVM Storage Pool 


see [http://libvirt.org/storage.html#StorageBackendLogical](http://libvirt.org/storage.html#StorageBackendLogical)

---

### Post by heiko_s on 2013-06-09
> **BostonDriver said:**
> LVM Volume Group is a perfectly valid type of KVM Storage Pool 


see [http://libvirt.org/storage.html#StorageBackendLogical](http://libvirt.org/storage.html#StorageBackendLogical)

Sorry, I wasn't clear. Of course LVM is a valid type of storage, under Xen (and perhaps kvm too) it's the preferred storage type. I'm using LVM for everything except the /boot partition, it makes storage management a lot easier.

---

### Post by heiko_s on 2013-06-09
> **BostonDriver said:**
> I'm looking to better understand the relationship between KVM and how it uses LVM Volume Group (VG) for a storage pool.

How does the LVM Volume Group relate to the rest of the system?   Is the VG dedicated  to KVM?  Or can Logical Volumes (LV) be created on this VG via lvcreate allowing filesystems to be used?

Thanks for any info.

Here some more specific answers:

KVM can use LV (logical volumes) as storage type. In that case you don't create a file system on the LV, but use your guest to create a file system. For example, my Windows 7 domU (guest) uses several NTFS-based partitions on LVM, all created from within the Windows guest.

With LVM you first create a PV (physical volume), for example:
```
pvcreate /dev/sda2
```

Then a VG (volume group):
```
vgcreate groupname /dev/sda2
```

Then a LV (logical volume) that is sort of a partition:
```
lvcreate -L 50G -n lvname groupname
```

KVM uses the LV(s) for storage. It doesn't matter in which VGs these LVs are, you can have multiple LVs in multiple VGs. In my case, I have a VG named "lm" that contains a LV named "win7" (this is the Windows 7 "C:" partition/drive), but I also have a VG named "data" containing LVs like "photos" and "raw". All the LVs mentioned here are used by my Windows guest.

My "lm" VG also contains the "root" and "home" LVs that are used by my Linux OS. Of course you could have different VGs for your host OS volumes and for your guests, it's up to you.

Is the VG dedicated  to KVM? Answer: no (see above). You use LVs, and yes, an LV would be dedicated to a drive/volume of your guest VM (see "win7" above).

Or can Logical Volumes (LV) be created on this VG via lvcreate allowing filesystems to be used? Answer: When using RAW storage in KVM or Xen you don't create a file system in the LV. This is done by the guest. You can access this storage from the host OS by using the kpartx command - just watch out, don't add/delete/modify files while the guest is running!!!!!! For an intro on how to use kpartx with Xen (or KVM) guests, see [http://forums.linuxmint.com/viewtopic.php?f=42&t=111783]("http://forums.linuxmint.com/viewtopic.php?f=42&t=111783").

For a good intro into LVM, see here: [http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/]("http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/")

Good luck!

---

