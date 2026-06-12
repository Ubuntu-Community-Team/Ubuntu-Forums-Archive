---
title: "XP VM freezing gutsy when booting after virtualbox update to 1.5.6"
date: 2008-02-24
forum: Virtualisation
---

### Post by fjf on 2008-02-24
This is the first program that is able to freeze gutsy.  Reminds me of Window$!.  Any known fix?.

---

### Post by Cannaregio on 2008-02-24
You don't explain exactly what happened.
For what it is worth:

If it is just frozen once
ALT+SYSRq+R+S+E+I+U+B will restart all frozen GNU/linuxes

If it is instead so, that you have a dual boot, say xp and GNU/Linux, and that a virtual memory loader in XP ruined everything and you cannot boot  anymore and don't see the grub (linux hdisk no more recognized) and you get instead, say, the dreaded "busybox" and inode problems, then

first check the exact name of your own disk and linux partition through any live-cd gparted... let's say it is sda1, that I will use in the code below, if it is not sda1, change accordingly.

Now use the following command (supposing yo have ext2 or ext3):

```
e2fsck -b 32768 /dev/sda1
```

Be prepared to answer a lot of Yes, after this the disk will be in order.

---

