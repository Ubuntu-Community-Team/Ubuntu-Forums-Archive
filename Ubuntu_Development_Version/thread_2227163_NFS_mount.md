---
title: "NFS mount"
date: 2014-05-31
forum: Ubuntu Development Version
---

### Post by P-I H on 2014-05-31
Mount of directories in my Ubuntu server from fstab stopped to work when I changed to systemd.
I found a solution on this site
[https://wiki.archlinux.org/index.php/NFS](https://wiki.archlinux.org/index.php/NFS)

I added these two options in the mount request in fstab
x-systemd.automount,x-systemd.device-timeout=10

The mount request now looks like this
```
192.168.0.123:/srv/Media /home/user/NASMedia nfs rsize=8192,wsize=8192,x-systemd.automount,x-systemd.device-timeout=10,timeo=14,intr 0 0
```

---

### Post by Elfy on 2014-05-31
Might be nothing, might be something - I'd report a bug with ubuntu-bug and add systemd-boot as a tag.

---

