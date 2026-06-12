---
title: "how to install slackware and keep my ubuntu?"
date: 2008-07-14
forum: Slackware and derivatives
---

### Post by sink on 2008-07-14
I already have ubuntu but I want to install slackware on another partition so that I can choose at boot time. how to do it?

---

### Post by kk0sse54 on 2008-07-14
Google. Really it's as simple as a quick search.All you need to do is partition your hard drive and install slackware on the other partition. Then if you choose to install Lilo you will have to edit Lilo boot loader to include Ubuntu.

---

### Post by saulgoode on 2008-07-14
I would recommend installing Slackware as normal (to its own partition) but when you get to the part (near the end of the process) where it asks about installing LILO, select the option to "Install to partition's boot record". DO NOT INSTALL LILO to the MBR (master boot record).  

This will permit you to modify GRUB to add the Slackware partition later.

---

### Post by kk0sse54 on 2008-07-14
> **saulgoode said:**
> I would recommend installing Slackware as normal (to its own partition) but when you get to the part (near the end of the process) where it asks about installing LILO, select the option to "Install to partition's boot record". DO NOT INSTALL LILO to the MBR (master boot record).  

This will permit you to modify GRUB to add the Slackware partition later.

:lolflag::lolflag: really take that advice I can tell you from the first time I installed slack adding another linux os to grub is a lot easier than Lilo.

---

### Post by Yuki_Nagato on 2008-07-14
I got away with this GRUB configuration initially.

```
title Slackware
root (hd0,0)
kernel /boot/vmlinuz root=/dev/hda1 ro vga=normal
```

I do not know why the second root needs to be +1.  Nor do I know how this handles multiple kernels (as I have had no kernel updates yet).

---

### Post by kk0sse54 on 2008-07-15
[]("http://ubuntuforums.org/showthread.php?t=724817")[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817) take a look at that otherwise you are going to have to manually edit grub for every new kernel you get.

---

