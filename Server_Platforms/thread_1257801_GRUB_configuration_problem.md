---
title: "GRUB configuration problem"
date: 2009-09-04
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-09-04
I have a server running RAID1 that I am trying to configure GRUB on, so that the machine will re-boot if either disk fails.
The command sequence I have for this is:
```
# grub
grub> (hd0,0)
grub> root (hd0,0)
grub> setup (hd0)
grub> (hd1,0)
grub> root (hd1,0)
grub> setup (hd1) 
```
then grub install can be checked using
```
# grub
grub> find /boot/grub/stage1
```

However once in grub I'm getting a series of errors:
```
# grub
grub> (hd0,0)
Error 27: Unrecognized command

grub> root (hd0,0)
Error 21: Selected disk does not exist

grub> find /boot/grub/stage1
Error 15: File not found

```

Anyone any ideas what is happening/what I'm doing wrong?

---

