---
title: "clean your hard drive on your computer"
date: 2009-11-15
forum: Security
---

### Post by soni1 on 2009-11-15
**[B]How do you clean your hard drive on your computer with no virus protection?**[/B]

---

### Post by wilee-nilee on 2009-11-15
What is the OS? and what are you trying too clean? in other words what is it your trying to achieve?

---

### Post by HermanAB on 2009-11-16
Data Definition can zap a disk and then you need to re-install of course:
$ sudo dd if=/dev/zero of=/dev/sdX bs=1M

Do yourself a favour and read the dd man page first.

---

### Post by witeshark17 on 2009-11-16
> **HermanAB said:**
> Data Definition can zap a disk and then you need to re-install of course:
$ sudo dd if=/dev/zero of=/dev/sdX bs=1M

Do yourself a favour and read the dd man page first. This will totally zero the drive, there will be 
nothing on it, not even a boot record; look for other options first IMO.

---

### Post by blazemore on 2009-11-17
if you want to destroy a drive (/dev/sda1), do this from a liveCD
```
sudo dd if=/dev/urandom of=/dev/sda1
```

Leave that for ages.

Then physically remve the drive from your computer, and run a powerful magnet over it lots of times.

Then hit it repeatedly with a hammer, and dispose of the parts in separate locations at different times.

or melt it down in a high temperature blast furnace and make something out of it.

---

