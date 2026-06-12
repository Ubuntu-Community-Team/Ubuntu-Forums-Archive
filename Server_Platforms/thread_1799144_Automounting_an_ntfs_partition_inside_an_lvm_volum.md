---
title: "Automounting an ntfs partition inside an lvm volume"
date: 2011-07-07
forum: Server Platforms
---

### Post by pakezonite on 2011-07-07
Hi!

I have an lvm volume group VG_GUESTS and inside it a
logical volume LV_NTFSDATA that was connected to and
formatted to NTFS by a guest virtual machine (KVM). 

I can mount the 1st NTFS partition on that lv manually like this:

```

sudo kpartx -a /dev/VG_GUESTS/LV_NTFSDATA
sudo mount -t ntfs-3g /dev/mapper/VG_GUESTS-LV_NTFSDATA1 /mnt/NTFSDATA1

```However, I would like this to happen at boot time automatically -how do I do that?

/P

---

### Post by drr422 on 2011-08-06
> **pakezonite said:**
> Hi!

I have an lvm volume group VG_GUESTS and inside it a
logical volume LV_NTFSDATA that was connected to and
formatted to NTFS by a guest virtual machine (KVM). 

I can mount the 1st NTFS partition on that lv manually like this:

```

sudo kpartx -a /dev/VG_GUESTS/LV_NTFSDATA
sudo mount -t ntfs-3g /dev/mapper/VG_GUESTS-LV_NTFSDATA1 /mnt/NTFSDATA1

```However, I would like this to happen at boot time automatically -how do I do that?

/P


I wish I could find this out as well.  I have added the LVM to fstab, yet it doesn't mount on boot. I have to manually mount it each time.

---

