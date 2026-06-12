---
title: "Error 13: Invalid or un supported executable format"
date: 2010-08-04
forum: Server Platforms
---

### Post by Shadowfire on 2010-08-04
First alittle about my system:

Ubuntu 9.04 server (64bit)
8GB
(2) 320 WD HDD - RAID 1

After coming home one evening I found my server was turned off.  My suspicions lead me to believe we had a storm and the power went off, then the UPS went off and finally at that point the server went off too. I think my server was set to allow security updates. After it turned of and restarted it seems it made a change to Grub and upgraded it to Grub2. In doing so I now get the following message:

Error 13:  Invalid or un supported executable format

I have tried to do the following:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331)

-------------

This solved the problem for me, from > [http://ubuntuforums.org/showpost.php?p=6977997&postcount=5](http://ubuntuforums.org/showpost.php?p=6977997&postcount=5)

Quote:
boot from the live medium and chroot into the Linux installation:

$ sudo mkdir /mnt/linux
$ sudo mount -t ext4 /dev/sda1 /mnt/linux
$ sudo mount -t proc proc /mnt/linux/proc
$ sudo mount -t sysfs sys /mnt/linux/sys
$ sudo mount -o bind /dev /mnt/linux/dev
$ sudo chroot /mnt/linux

If /boot is on a separate partition, this partition must also be mounted:

$ sudo mount -t ext4 /dev/sdaX /boot

Then, the following command should resolve the issue. :

$ sudo grub-install --recheck /dev/sda

------------

unfortunately it didn't work and said it could not find device.  Anyone able to help me figure out what to do next?

Thx
SF

---

### Post by ruffEdgz on 2010-08-04
Did you get any errors or logs that stated it didn't work. I did the following command on my system and it said this:
```

grub-install --recheck /dev/sda
Installation finished. No error reported.

```
If you can, you might want to show your grub.cfg file that relates to which Ubuntu is booted. Here is an example of what mine looks like:
```

menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 22f1d1b3-7a47-4e9e-990c-62da1fa3eb66
        linux   /vmlinuz-2.6.32-24-generic root=/dev/mapper/sys_vg-slash ro rootdelay=10  quiet splash
        initrd  /initrd.img-2.6.32-24-generic
}

```

---

### Post by Shadowfire on 2010-08-04
Ok. My fault - I cut off the last part of where I got to... 

when typing in and invoking command:
sudo mount -t ext4 /dev/sda1 /mnt/linux

I recieved the following error:
mount: special device /dev/sda1 does not exist

-------

But when I do:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38882   312319633+  8e  Linux LVM
/dev/sda2           38883       38913      249007+   5  Extended
/dev/sda5           38883       38913      248976   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bcf

So I am guessing my command logic is not correct, and I am wondering what my command logic should be if the sudo mount -t ext4 /dev/sda1 /mnt/linux gives me the mount: special device /dev/sda1 does not exist. error.

Thoughts are greatly appreciated.

Thx,
SF

---

### Post by Shadowfire on 2010-08-07
I still have not been able to figure out the answer to this issue.  I was able to get past the mount: special device \dev\sda1 does not exist.

I did:
cd /dev
MAKEDEV sda

It made multiple sda* 

under fdisk -l I still see:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bcf

Device Boot Start End Blocks Id System
/dev/sda1 1 38882 312319633+ 8e Linux LVM
/dev/sda2 38883 38913 249007+ 5 Extended
/dev/sda5 38883 38913 248976 83 Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bcf

Device Boot Start End Blocks Id System
/dev/sdb1 1 38882 312319633+ 8e Linux LVM
/dev/sdb2 38883 38913 249007+ 5 Extended
/dev/sdb5 38883 38913 248976 83 Linux

--- 

Now when I try to do: 
sudo mount -t auto /dev/sda1 /mnt/linux

I get:
mount: \dev\sda1 is not a block device

I tried mounting sda2, sda3 and so on but still get block device error.

Any ideas on this - remember this system is RAID 1 configuration.

Thanks,
SF

---

### Post by FuturePilot on 2010-08-07
/dev/sda1 is LVM. You need to open the LVM before you can access the file system.

[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html]("http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html")

---

