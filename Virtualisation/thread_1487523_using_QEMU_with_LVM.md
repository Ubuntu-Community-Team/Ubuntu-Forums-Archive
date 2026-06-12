---
title: "using QEMU with LVM"
date: 2010-05-19
forum: Virtualisation
---

### Post by tapas_mishra on 2010-05-19
I am having a small confusion which I do  not know how to get rid of.
I  have to install Ubuntu on a machine for some experiment.I am using QEMU
I did 
```

dd of=hd.img bs=1024 seek=6000000 count=0
 qemu-system-x86-64  -boot d -cdrom /dev/cdrom  -hda hd.img

```
Every thing is working perfectly find as desired.I am able to install.
But 
1) I want to use an LVM instead of hard disk image.
2) and want to export this QEMU installation to use on Xen.
This I am not clear with.

---

