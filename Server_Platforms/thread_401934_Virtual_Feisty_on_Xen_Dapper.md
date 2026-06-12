---
title: "Virtual Feisty on Xen Dapper"
date: 2007-04-05
forum: Server Platforms
---

### Post by seppe on 2007-04-05
I'm using Xen on Dapper: creating virtual images of other Dapper servers with xen-create-image.

I would like to create Feisty images using the same procedure but the command (note the --dist="feisty" option):
```

sudo xen-create-image --debootstrap="--arch i386" --dist="feisty" --dir=/xen-images/ --swap=256Mb --size=2Gb --mirror="http://archive.ubuntu.com/ubuntu" --passwd --fs=ext3 --memory=256Mb --kernel=/boot/vmlinuz-2.6-xen -ip 192.168.0.200 --gateway 192.168.0.1 --netmask 255.255.255.0 --hostname=feistytest

```
passes over the debootstrap installation with no effect: I think debootstrap on Dapper can't create Feisty installations.

**Is there a way to install Feisty using debootstrap from Dapper?**

Thanks.

---

