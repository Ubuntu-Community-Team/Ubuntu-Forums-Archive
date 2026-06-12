---
title: "Mounting usb in OpenVZ VPS"
date: 2009-03-15
forum: Virtualisation
---

### Post by starfry on 2009-03-15
Hello,

I have a running VPS built from the 8.04 minimal template.

I have enabled a USB flash device and made the mount point:

```
  
# vzctl set 247 --devices b:8:33:rw
# vzctl exec 247 mknod /dev/sdc1 b 8 33

```

But I can't mount it:

```

root@vz247:~# mount /dev/sdc1 /mnt
mount: you must specify the filesystem type
root@vz247:~# mount -t vfat /dev/sdc1 /mnt
mount: unknown filesystem type 'vfat'
root@vz247:~# mount -t msdos /dev/sdc1 /mnt
mount: unknown filesystem type 'msdos'
root@vz247:~#

```

My kernel is the standard one from the OpenVZ apt package:

```

root@vz247:~# uname -a
Linux vz247 2.6.24-24-openvz #1 SMP Thu Feb 19 11:08:06 UTC 2009 i686 GNU/Linux
root@vz247:~# 

```

I can mount it successfully on the HE with a simple
```

root@he240:~# mount /dev/sdc1 /mnt
root@he240:~#

```


Any ideas what am I doing wrong?

Thanks!

---

### Post by starfry on 2009-03-17
Bind mounting is the solution: Mount as normal on the HE and then bind mount to /vz/root/vps_id/....

---

