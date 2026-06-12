---
title: "Initial ramdisk"
date: 2010-05-10
forum: Server Platforms
---

### Post by Linux000 on 2010-05-10
Hi, I have an install of Ubuntu Server 10.04(upgrade from 9.10), I installed a new hard drive on the primary IDE of my server, and forgot to set it to slave, so the BIOS was very confused, I set the hdd to slave, and now the Initial Ramdisk of ubuntu can't find the Partition and times out to a low-level prompt, from here I can mount the disk, and all the data is there, even the file the ramdisk can't find. Does anyone know how to fix this? Also, it is a 32bit computer.

---

### Post by koenn on 2010-05-11
it would be good if you can post the actual text on your screen in stead of vague references to 'a low-level prompt', because most of what you say doesn't make sense at all (eg. the initialm ram disk is not expected to 'find' files or partitions)

maybe just running ```
update-grub
``` will fix your problem, but it's hard to say without knowing what state your computer is in after its boot.

---

### Post by Linux000 on 2010-05-11
Okay, I'll try again.
Here is what the screen says when it boots...

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /pro/cmdline)
  - Check rootdelat= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/95e9b43f-966e-4e08-a7c7-3024c804c760 does not exist. 
Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help for a list of built in commands.

(initramfs) 

```
And here is what running update-grub says...
```

/bin/sh: update-grub: not found
(initramfs) 

```

Also...

The UUID is correct (in the /dev/disk/by-uuid path)
And running cat ```
/proc/cmdline 
``` gives ```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-20-server root=UUID=95e9b43f-966e-4e08-a7c7-3024c804c760 ro quiet splash
```
And mounting the disk with ```
mount /dev/disk/by-uuid/95e9b43f-966e-4e08-a7c7-3024c804c760 /media
```
mounts the device and all the data is there

---

### Post by koenn on 2010-05-13
ok, try this:

```

mount /dev/disk/by-uuid/95e9b43f-966e-4e08-a7c7-3024c804c760 /
/usr/sbin/update-grub

```

then reboot and see what gives

---

### Post by Linux000 on 2010-05-13
I can't seem to mount the drive to root, the device is busy, and update-grub returns an error if I mount the disk to a file(can't find another file).

---

### Post by frostschutz on 2010-05-13
what does 'ls -l /dev/disk/by-uuid' give you?

maybe the uuid is actually different and that's why it can't find it

EDIT: just read that you said the mount works if you do it manually. that's definitely odd then...

---

### Post by Linux000 on 2010-05-13
Yes, the mount works, and the UUID is correct, I can mount the same uuid on /media (folder I created), but I can't mount it to root, is returns ```
mount: mounting /dev/disk/by-uuid/95e9b43f-966e-4e08-a7c7-3024c804c760 on / failed: Device or resource busy
```

---

### Post by koenn on 2010-05-16
if it's already mounted on /media, you may need to unmount it first
also, don't cd /media, because then this becomes your working directory, and the underlying partition will always be 'busy'.

what do you get from 'mount' in busybox ?

---

### Post by Linux000 on 2010-05-16
I unmounted the disk from /media and mounted it to / , but root show the same files as before, not want was in my root partition. And I'll have to wait until I get to a real computer to type what it says when I run mount, but there are to devices(rootfs and /dev/sda1(where the other file links to) mounted to root

---

### Post by helferlein on 2010-05-17
Hello I have an initial ramdisk problem too!

My problem is copiing a (still-working) sda1/boot to sdb1/boot and boot from there and also ended up in busy-box. So I try to recreate an i-ramdisk still no luck.

But there seems to be a bug !

do you have a file /etc/initramfs-tools/conf.d/resume ?

In some of my Lucid-Installations there is an invalid uuid pointing to a swap device. I have renamed the file to resume.old for the moment since I do not use swap files at all.

It didn't fix my problem, but may help you

---

### Post by Linux000 on 2010-05-24
Sorry that it took so ling to reply. Unfortunately, I do not have an /etc/initramfs-tools directory. Thanks for your help!

---

