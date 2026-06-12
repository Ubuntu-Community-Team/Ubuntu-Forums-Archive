---
title: "KVM external snapshots of VMs"
date: 2024-05-01
forum: Virtualisation
---

### Post by aljames2 on 2024-05-01
I am trying to learn about libvirt external snapshotting of VM qcow2 images.  I think I prefer this vs internal snapshots where the snapshot lives inside the qcow2 file because the qcow2 file grows rapidly with each snapshot and even if you delete a snapshot inside the image file you can't recover that space to reduce the image file, that I've discovered..

External snapshots at least give some more control over disk space; however, the downside is that while external snapshots can be easily created, there is no integration yet in virt-manager, nor does virsh revert work with external snapshots. So, manual methods are needed to revert a VM image from an external snapshot.  At least this is how I understand things so far.

Curious if anyone is already doing external snapshots of their VMs, and how that has been working out? I have written a recipe for creating external snapshots, just need to work on how to revert from an external sn.

I have read this page on the topic.
[https://wiki.libvirt.org/I_created_an_external_snapshot_but_libvirt_will_not_let_me_delete_or_revert_to_it.html](https://wiki.libvirt.org/I_created_an_external_snapshot_but_libvirt_will_not_let_me_delete_or_revert_to_it.html)

My thought is it would be good to keep a few snapshots on hand in case I break something in a VM, and since my backup process will always overwrite the previous backup of an image, there is a chance I could backup up a broken VM and have nothing viable to revert to.  A few snapshots would help in this case I think.

My KVM host is ext4-LVM and my VMs are qcow2 images.

Hmmm, could LVM snapshots be an option because all my VMs are in their own logical volume.  Hmmm ?

---

### Post by MAFoElffen on 2024-05-01
@aljames --

LOL. Thinking about your system, and what is relatable.

Yes, you can recover space from provisioned thin qcow vdisks after they grow, and you have made room in them, then sparsifying it, then...
```

qemu-img convert -f qcow2 -O qcow2 -c orig.qcow2 new.qcow2

```
But that only works if there are no KVM snapshots... With conflicts with other things you talked about. 

I've done external snapshots of VM's by creating a ZFS pool for VM's, then creating the VM drives as ZFS datasets. Then snapshoting the dataset (vdisk).

I've also added LVM2 to my ZFS-On-Root machine and done KVM LVM2 VG storage pools, then provisioned the vdisks as LV's...

Both take up the same resources: Both ZFS pools & LVM2 VG's (VG's use PV extents)... Use a dedicated partition for that. (At least 1).

---

### Post by aljames2 on 2024-05-01
Lol, yep that's me :)

> **MAFoElffen said:**
> I've done external snapshots of VM's by creating a ZFS pool for VM's, then creating the VM drives as ZFS datasets. Then snapshoting the dataset (vdisk).

This I like and hadn't thought to try that on this box. My other tower is running all ZFS and there are VMs on that, with cron doing nightly snapshots and then sends to a bckpool.  So, I could use ZFS on this box for just for this purpose of housing my VMs and use the same ZFS tools.  Should I then have a separate disk for ZFS or can it play nicely with other filesystems on this same disk, separate partitions of course?

---

### Post by MAFoElffen on 2024-05-02
It can just be a standalone ZFS Pool on any type of Ubuntu root FS. ZFS, like LVM2, does not need a separate "disk"... All it needs is a separate "partition". I've had LVM2, and ZFS on the same "disk". Linux doesn't care. As long as you have the mountpoints coordinated, so it ca piece it all together seamlessly.

If you did have it on it's own disk, then you make it portable... That is can be exported/imported to a newer OS, or to other hardware. I do this with my workstation , and server... But both of those machines of mine have "drive bays" that make it convention to add/remove drives.

Doing that, Then you could Send/Receive snapshots, remotely between machines. I do have to admit, ZFS is more portable/transportable, than LVM2.

---

### Post by aljames2 on 2024-05-05
Thanks MAFoElffen.  I did get this done this weekend.  Set up a ZFS pool on an extra disk & created a separate dataset for each VM so that ZFS snapshotting will be VM specific, vs. all VMs in the same snapshot, if they all were in the same dataset.  I rsync’d my VM images into their respective datasets, then used virt-manager to “create new —> import image”.  Then after confirming the VMs work, ssh, everything seems intact.  Finally, virsh undefine the originals.

I was stumped for a bit thinking about how I could get virt-manager to use a “single” storage pool for VMs on a single zfs dataset, like I have been used to using other storage types. This is how my thinking started, especially when virt-manager gives an option to select ZFS pool as a storage type. Turns out, the “ZFS pool” option is not a working feature in virt-manager, as I understand.  Confusing that it is there.  The answer was to create a new zfs dataset for each VM, and then go into virt-manager and add a storage pool with type “directory filesystem”, and enter the mountpoint for the dataset.

---

