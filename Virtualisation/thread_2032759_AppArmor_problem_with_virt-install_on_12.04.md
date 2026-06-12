---
title: "AppArmor problem with virt-install on 12.04"
date: 2012-07-24
forum: Virtualisation
---

### Post by macalloy on 2012-07-24
I've installed 12.04 64bit with virtualization package.

when I try to create a virtual machine with

```

virt-install --name win7 --ram 4096 --vcpus=3 --cdrom=/dev/cdrom --os-type=windows --os-variant=win7 --disk /etc/libvirt/disk/win7.raw --vnc --noreboot

```

I get this error

```

Starting install...
ERROR    internal error cannot load AppArmor profile 'libvirt-3f46c2d6-217b-e054-1804-d9343ae14e40'
Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start win7
otherwise, please restart your installation.

```

Do I need to install another package or do some additional manual configuration?

Thanx!

---

### Post by macalloy on 2012-07-25
The problem was the path of the disk image.
It is not allowed to reside in /etc.
I've moved the image to 

```
/var/lib/libvirt/images
```

now it works as expected.

---

