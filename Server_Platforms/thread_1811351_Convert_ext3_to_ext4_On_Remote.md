---
title: "Convert ext3 to ext4 On Remote"
date: 2011-07-24
forum: Server Platforms
---

### Post by zemon_ on 2011-07-24
I need to convert my server(10.04) to ext4 from ext3 and want to make sure I am going to do this the correct way.

Edit fstab to ext4
```
sed -i s/ext3/ext4/ /etc/fstab
```

Run the tune2fs command, the filesystem is mounted is this ok?

```
tune2fs -O extents,uninit_bg,dir_index /dev/md0
tune2fs -O extents,uninit_bg,dir_index /dev/md2
```

Now reboot the system and a fsck will run automatically as the tune2fs command has been run.
```
reboot
```

Once the server comes back online
```
grub-install /dev/md0
```

Is this correct?

---

### Post by zemon_ on 2011-08-04
So changing the home partition to ext4 is very simple but how to change the root partition.

```
umount /dev/md2
```

```
e2fsck /dev/md2
```

```
tune2fs -O extents,uninit_bg,dir_index /dev/md2
```

```
e2fsck /dev/md2
```

now edit the /etc/fstab and reboot.

How can I unmount the root partition md0 if the root partition is always going to be in use.

---

### Post by Vegan on 2011-08-04
I find changes like your intentions can introduce problems

Might be safer to wait for the next LTS release and install it on a new machine with the desired file system. Then migrate your files using rsync.

In my experience its best to have a couple of virtual machines if you want to experiment.

---

