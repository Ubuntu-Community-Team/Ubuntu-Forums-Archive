---
title: "HP ML330 G6 not booting - sbin/init not found"
date: 2014-02-12
forum: Server Platforms
---

### Post by andrew-stewart on 2014-02-12
1 of 4 drives failed - replacement installed and logical drive rebuilt successfully - no other hardware faults. 
Ubuntu 9.10 server installed.

On boot, 1 logical drive found, but following messages appear and system halts... chroot: cannot execute /etc/apparmor/initramfs: No such file or directory run-init: /sbin/init: No such file or directory [ 20.252079] Kernel panic - not syncing: Attempted to kill init!

... any help most appreciated,
Andrew

---

### Post by brokenhachi on 2014-02-12
We need to know what your partition/drive layout looks like. Can you explain your drive layout, and maybe boot to livecd, mount the drives and print /etc/fstab? Also, did you change the UID for the drives in fstab after rebuilding the raid array? boot to livecd and to ```
blkid
``` to find the current UIDs, then match them up with /etc/fstab

---

### Post by andrew-stewart on 2014-02-17
> **brokenhachi said:**
> We need to know what your partition/drive layout looks like. Can you explain your drive layout, and maybe boot to livecd, mount the drives and print /etc/fstab? Also, did you change the UID for the drives in fstab after rebuilding the raid array? boot to livecd and to ```
blkid
``` to find the current UIDs, then match them up with /etc/fstab

Thanks for your reply. 

We have 4x 250GB drives in RAID 5.

I didn't change the UID for the drives in fstab after rebuilding the array -> I'm not sure how to.

I booted to livecd and hope the following information helps...

/target # mount
rootfs on / type rootfs (rw)
none on /proc type proc (rw,relatime)
none on /sys type sysfs (rw,relatime)
tmpfs on /dev type tmpfs (rw,relatime)
devpts on /dev/pts type devpts (rw,relatime,mode=600,ptmxmode=000)
/dev/2/root on /target type ext4 (rw,relatime,barrier=1,data=ordered)
tmpfs on /target/dev type tmpfs (rw,relatime)
none on /target/proc type proc (rw,relatime)
none on /target/sys type sysfs (rw,relatime)

/target # fdisk -l

Disk /dev/cciss/c0d0: 750.1 GB, 750077009920 bytes
255 heads, 63 sectors/track, 91191 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8bd9

                 Device Boot   Start     End       Blocks             Id   System                
/dev/cciss/c0d0p1          1           91161   732242668+   8e  Linux LVM
/dev/cciss/c0d0p2          91161   91191   249007+         5    Extended
/dev/cciss/c0d0p5          91161   91191   248976           83   Linux

/target # blkid
/dev/cciss/c0d0p1: UUID="a5ik2Y-..." TYPE="LVM2_memer"
/dev/cciss/c0d0p5: UUID="6c187489-..." TYPE="ext2"
/dev/mapper/z-root: UUID="611de0fz-..." TYPE="ext4"
/dev/mapper/Z-swap_1: UUID="c87060b4-..." TYPE="swap"


/target # cat /etc/fstab
none   /dev/pts   devpts   defaults   0    0
none   /proc        proc       defaults   0    0
none   /sys         sysfs      noauto     0    0

---

### Post by brokenhachi on 2014-02-22
Hey there. I got you message and sorry for the late reply. I actually don't know a lot about LVM, but the general idea applies: You need to have your mountpoints referenced in /etc/fstab.

```
 % cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
#Entry for /dev/sda5 :
UUID=f69e96f4-8a45-4921-8778-48c83947e226       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sda7 :
UUID=ceeb74c2-629c-499e-b900-ce7df2715aca       /boot   ext2    defaults        0       2
#Entry for /dev/sda6 :
UUID=c52bf6fa-061a-4917-a47c-506afe6d7ffe       none    swap    sw      0       0

```

above is the example of my fstab. You'll need to have in your a line for /boot, /, and swap in order to correctly boot the system. The error you are receiving is that the system doesnt know where to find initramfs because you haven't told it where /boot is in fstab i think.

you can manually edit /etc/fstab and add the above lines like in mine, but change the uuid to the referenced disk. My guess is the ext4 partition above is / and the ext2 partition is /boot (as that is the default). though please properly mount the lvm in livecd and check the uuids/partitions.



edit: i found this that might help you map fstab correctly for lvm. you can use devs instead of UUIDs ;)

```
duxon@rolfgang:~% cat /etc/fstab
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
# /dev/mapper/main-root
/dev/mapper/main-root     /         	ext4      	rw,relatime,data=ordered	0 1

# /dev/mapper/main-home LABEL=home
/dev/mapper/main-home     /home     	ext4      	rw,relatime,data=ordered	0 2

# /dev/sda1
UUID=91d776eb-1cf4-4437-a06e-f6a86ee7d0fb	/boot     	ext4      	rw,relatime,data=ordered	0 2

#swap
UUID=6ccf4f96-a05f-4e71-b864-7652e3684c23 	none	swap	defaults,discard	0 0
```

[https://bbs.archlinux.org/viewtopic.php?id=172384](https://bbs.archlinux.org/viewtopic.php?id=172384)

---

### Post by andrew-stewart on 2014-02-24
Thanks for your reply brokenhachi.

From your pointer, I went to edit /etc/fstab and found (as copied in my previous post), I had typed "cat **/**etc/fstab" from target instead of "cat etc/fstab"!!

So, here is how fstab really looks just now:

<file system>   <mount point>   <type>   <options>   <dump>   <pass>
proc   /proc   proc   defaults   0   0
/dev/mapper/2-root   /   ext4   errors=remount-ro   0   1
# boot was on /dev/cciss/c0d0p5 during installation
UUID=6c187489...   /boot   ext2   defaults   0   2
/dev/mapper/2-swap_1   none   swap   sw   0   0
/dev/scd0   /media/cdrom0   udf,iso9660   user,noauto,exec,utf8   0   0

And I also noticed I made a couple of typos in my last blkid paste, so here's how it really looks just now:

/target # blkid
/dev/cciss/c0d0p1: UUID="a5ik2Y-..." TYPE="LVM2_memer"
/dev/cciss/c0d0p5: UUID="6c187489-..." TYPE="ext2"
/dev/mapper/2-root: UUID="611de0fz-..." TYPE="ext4"
/dev/mapper/2-swap_1: UUID="c87060b4-..." TYPE="swap"

So, it seems ok and it's not fstab that's causing the problems and so I'm back to square one with trying to interpret the messages at boot:

[I]chroot: cannot execute /etc/apparmor/initramfs: No such file or directory run-init: /sbin/init: No such file or directory [ 20.252079] Kernel panic - not syncing: Attempted to kill init!

[/I]I'm not sure what to try next and would be very grateful for any further suggestions.

---

### Post by brokenhachi on 2014-02-24
In that case i think you need to do grub recovery. I found this post via google: [http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd](http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd)

I don't think you need to install the lvm2 package or whatever they are talking about so, can you boot again to livecd and please do the following:

mount the lvm:
```
mkdir /mnt/oldlvm
mount /dev/mapper/2-root /mnt/oldlvm
mount /dev/cciss/c0d0p5 /mnt/oldlvm/boot
mount -o bind /dev /mnt/oldlvm

```

chroot to the old lvm:
```
chroot /mnt/oldlvm

```

update initramfs and grub:
```
update-initramfs -u
update-grub
```

Then please try reboot. If it doesn't work then maybe you do need to install the lvm2 package under the chroot in livecd.

---

### Post by andrew-stewart on 2014-02-28
Many thanks for your ongoing help brokenhachi - this looked like a good plan, but I ran into another hurdle...

After mounting, I tried the chroot but it's returning the following...
[B]chroot: cannot execute /bin/sh: No such file or directory

[/B]The folders/files are as follows:/bin/sh->busybox
/usr/sbin/chroot->/bin/busybox
/target/bin/sh->dash
/target/usr/sbin/chroot

So I tried this but the result was the same:
chroot /mnt/oldlvm /target/usr/sbin

I've also tried 3 live CDs versions (server x64, alternative x64 with the same results, and desktop x64 didn't boot).

Hope you may be able to help again.

---

