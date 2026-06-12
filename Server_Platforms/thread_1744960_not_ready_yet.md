---
title: "/ not ready yet"
date: 2011-04-30
forum: Server Platforms
---

### Post by Vegan on 2011-04-30
So what gives with the / not ready yet?

Is there some disk error I need to fix?

Disk itself is fine, this seems to be a file system problem.

---

### Post by sikander3786 on 2011-04-30
Might be some problem with /etc/fstab. You might need to chroot your install from a Live CD and make some changes.

If there are not a lot of settings/configurations installed, a fresh install will be less time consuming.

---

### Post by Vegan on 2011-04-30
I booted a live CD, the 255MB partition is visible, noting else shows us at all.

Is there maybe a problem with the grub setup?

I would like to be able to mount my disk again so I can bring my server back up

---

### Post by sikander3786 on 2011-04-30
Go to Applications > Accessories > Terminal from the Live CD and post the output of this command.

```
sudo fdisk -lu
```

---

### Post by Vegan on 2011-04-30
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018737

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM
ubuntu@ubuntu:~$

---

### Post by Vegan on 2011-04-30
Looking around with Google found little of help


> The disk drive for /mnt/foobar is not ready yet or not present.
Continue to wait; or press S to skip mounting or M for manual recovery 


Is the exact error I get from a cold boot

---

### Post by sikander3786 on 2011-05-01
Yes that error is a result of something bad in /etc/fstab maybe. From Terminal, type,

```
gksudo nautilus
```

Navigate to your old '/' partition, open up 'etc' directory and copy/paste all text from the file named 'fstab' please.

---

### Post by koenn on 2011-05-01
> **Vegan said:**
> So what gives with the / not ready yet?

Assuming this happens during system startup (you could have given a bit more info there...), 
this means your / partition isn't mounted (yet) by the time the boot routine wants to switch from initramfs to the / on your harddisk

to troubleshoot this, you need to find out why / isn't mounting. 

Is this related to your other thread with the massive file system corruption ?  That would explain it.

---

### Post by Vegan on 2011-05-03
I gave up on it after several hours, see my other thread.

---

