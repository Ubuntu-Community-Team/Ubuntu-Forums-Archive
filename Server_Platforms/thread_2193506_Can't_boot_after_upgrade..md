---
title: "Can't boot after upgrade."
date: 2013-12-13
forum: Server Platforms
---

### Post by Raptor Ramjet on 2013-12-13
Hello,

I tried to do a release upgrade on my home server the other day, from 11.10 to 12.04, after which it will not boot.  The file system appears to be present as I can view it from a live CD but grub fails with an "Error 15 File Not Found" message.  I've tried using the grub menu and have tried using all the listed kernel images (there are about 6 present) but none of them work (including the recovery console options) and they all fail with the same "Error 15 File Not Found" message.

Additionally I've tried manually running grub from it's command line by doing the following:

```

grub> find /grub/stage1

root (hd0,2)

grub> root (hd0,2)

grub>kernel (hd0,2)/boot/<TAB>


```

But this gives me the same "Error 15 File Not Found" message.

Following this I also tried reinstalling grub which seemed to suggest it worked but after rebooting I still get the same "Error 15 File Not Found" message.  I am confident that there is no hardware problem as the box has been running fine for about 5 years now and the S.M.A.R.T. on the disk shows it to be fine (it was running splendidly until I tried the dist upgrade).

At this point I have taken a copy of my /etc directory so if this can't be fixed I could do a reinstall but I would like to fix it if possible.  So if anyone has any ideas what to try I'd be most grateful ?

Failing that I would like to know if it's possible to reinstall from an Ubuntu server CD without formatting the disk (I've just downloaded the 12.04 CD) ?

Cheers.

---

### Post by houstonbofh on 2013-12-13
Is it a large hard drive on an old motherboard?  If so, it may have loaded the new boot image in a part of the drive the BIOS can't see...

---

### Post by pascalfares on 2013-12-13
Try boot-repair and follow instructions here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

