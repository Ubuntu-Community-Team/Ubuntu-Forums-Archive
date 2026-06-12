---
title: "Issues removing an mdadm array"
date: 2014-12-09
forum: Server Platforms
---

### Post by MakOwner on 2014-12-09
I'm trying to wipe a mdadm config and it's like a bad penny and just keeps coming back after reboots.

I stopped the array, then removed it.
mdadm --stop /dev/mdx
mdadm --remove /dev/mdx

Removed the array line from /etc/mdadm/mdadm.conf
Then I removed the partition on each drive and recreated a different partition with a different partition type.

I ran 
update-initramfs -u -k all
update-grub

The array was named md2, and after reboot it comes back as md127 -- so something is still being found during boot.

I'd just remove mdadm altogether, but I need it still.

---

### Post by rubylaser on 2014-12-10
You need to zero the superblock on the disks that were in the array, or as long as mdadm is installed, it will try to re-assemble your array.

```

mdadm --stop /dev/md0
mdadm --zero-superblock /dev/sdX1

```

---

### Post by MakOwner on 2014-12-10
Thank you. 
This is the step I was missing.

---

