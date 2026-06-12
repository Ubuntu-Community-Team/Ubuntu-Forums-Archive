---
title: "[XEN] DomU install from an ISO file"
date: 2008-06-12
forum: Virtualisation
---

### Post by Gillo on 2008-06-12
I'm trying to setup a domU directly from an ISO file built around isolinux (it's Endian Firewall).
After some googling, I found that Xen could boot ISO files but there is not much documentation available.
I did the following:

```
losetup `losetup -f`img.iso
losetup -a
/dev/loop0: [0303]:195853 (img.iso)

```

the content of my domU config file is the following:

```

kernel      = '/boot/vmlinuz-2.6.24-18-xen'
ramdisk     = '/boot/initrd.img-2.6.24-18-xen'
memory      = '128'
name='fw-inst'
disk=['tap:aio:/home/xen/domains/fw/disc.img,hda1,w','phy:/dev/loop0,hdc,r']
root = '/dev/hdc ro'
#vif = [ 'mac=AA:11:22:33:44:55', 'mac=AA:11:22:33:44:44']
pci = ['02:00.0']
extra = "4 noirqdebug"
on_reboot ='destroy'
```


the domU boots and I'm dropped to a busybox shell after a message stating that /sbin/init could not be found.
Once in the busybox shell, I can browse in the iso image directory structure so it's mounted correctly.
What did I do wrong? I'm using Xen 3.2 on Hardy Server.
Thanks in advance.

PS: my CPU is not VT enabled if that matters

---

