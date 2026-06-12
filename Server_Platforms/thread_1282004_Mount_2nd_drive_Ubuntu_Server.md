---
title: "Mount 2nd drive Ubuntu Server"
date: 2009-10-03
forum: Server Platforms
---

### Post by NJC on 2009-10-03
Trying in vain to mount a 2nd hard drive on Ubuntu server 9.04. Fdisk:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4835    38837106   8e  Linux LVM
/dev/sda2            4836        4866      249007+   5  Extended
/dev/sda5            4836        4866      248976   83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         637     5116671   83  Linux
/dev/sdb2             638        8961    66862530    b  W95 FAT32
/dev/sdb3            8962        9599     5124735   83  Linux
/dev/sdb4            9600        9729     1044225   82  Linux swap / Solaris

Here's line in Fstab:

```
/dev/sdb2       /media/backup  vfat defaults,user,dmask=027,fmask=137 0 0
```But I run mount to check and it's not there. What obvious thing am I missing????:confused:

EDIT: Oops, I had forgot to mkdir the folder.

---

### Post by swerdna on 2009-10-04
It's more common to use one of these forms:
[LIST]
[*]for everone: /dev/sdb2     /media/backup     vfat     umask=0000,utf8     0 0
[*]for just wilma:  /dev/sdb2     /media/backup     vfat     uid=wilma,gid=wilma,utf8     0 0
[/LIST]

I wonder if the option "user" which makes the partition mountable by anyone is getting in the way (don't know enough about it to be sure). Try running the command "sudo mount -a" to see if there's an error message thrown up.

FFI read here: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by NJC on 2009-10-04
Thanks Swerdna - I had copied from [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  but this line was problematic:

/dev/sdb2       /media/backup  vfat defaults,user,dmask=027,fmask=137 0 0

Not only did I want to make a mount point on the partition, but also view the partition too. The following allowed me to do it FINALLY. \\:D/

/dev/sdb2       /media/backup    vfat         rw,dmask=0000,fmask=0111    0  0

Found here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

