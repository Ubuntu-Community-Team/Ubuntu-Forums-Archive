---
title: "iPod Linux Help"
date: 2008-03-06
forum: The Cafe
---

### Post by money2themax on 2008-03-06
I'm trying to install iPod linux on a 30Gb White 5.5G iPod and i need pointer also i need to portion the ipod for either HFS+ or Ext2 i have the ability to read and write to both i have al the libs installed

---

### Post by money2themax on 2008-03-06
Meow!

---

### Post by aktiwers on 2008-03-06
Why not use the installer?
:)

---

### Post by money2themax on 2008-03-06
> **aktiwers said:**
> Why not use the installer?
:)
i tried it needs me to partition the iPod HDD

---

### Post by money2themax on 2008-03-06
Meow!

---

### Post by money2themax on 2008-03-06
this is how far i've gotten

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@MX-UBUNTU-000:~# ./ipodpatcher --scan
ipodpatcher v2.0 with v2.0 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Scanning disk devices...
[INFO] Ipod found - Video (aka 5th Generation) ("winpod") - /dev/sdg
root@MX-UBUNTU-000:~# ./ipodpatcher -r bootpartition.bin
ipodpatcher v2.0 with v2.0 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Scanning disk devices...
[INFO] Ipod found - Video (aka 5th Generation) ("winpod") - /dev/sdg
[INFO] Reading partition table from /dev/sdg
[INFO] Sector size is 2048 bytes
[INFO] Part    Start Sector    End Sector   Size (MB)   Type
[INFO]    0              63         48194        94.0   Empty (0x00)
[INFO]    1           48195      14651278     28521.6   W95 FAT32 (0x0b)
[INFO] Ipod model: Video (aka 5th Generation) ("winpod")
[INFO] Writing 48132 sectors to output file
[INFO] Done.
[INFO] Partition extracted to bootpartition.bin.
root@MX-UBUNTU-000:~# umount /dev/sdg2
root@MX-UBUNTU-000:~# umount /dev/sdg
umount: /dev/sdg: not mounted
root@MX-UBUNTU-000:~# fdisk /dev/sdg
Warning: Device /dev/sdg has a logical sector size of 2048.  Not all parts of
GNU Parted support this at the moment, and the working code is HIGHLY
EXPERIMENTAL.

Error: Unable to open /dev/sdg - unrecognised disk label. 
```

---

### Post by money2themax on 2008-03-06
this is what i'm trying to do

[http://ipodlinux.org/Manual_Installation](http://ipodlinux.org/Manual_Installation)

but im gonna do it with this prog i just need help setting it up
```

mke2fs

```

---

