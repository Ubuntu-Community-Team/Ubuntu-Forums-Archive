---
title: "Windows is refusing to boot, giving strange error"
date: 2008-08-29
forum: Windows
---

### Post by King_Critter on 2008-08-29
So today I tried to boot into windows. It didn't work, giving me a "disk read error." I Googled for information, but everything I could find indicated that the drive was failing. I know this isn't the case, because Linux works just fine, and the data on the Windows partition was completely intact. I tried reinstalling Windows -- no luck; I got the same error. I backed up everything important, formated the partition, and installed Windows. Same error. I formated the partition as Fat32 and installed Windows. Same error. I formated the partition using Gparted, rather then the partitioner that's on the Windows cd, and installed Windows. Same freaking error. So I gave up, restarted my computer... and then at the grub menu I decided to give Windows one more chance, and... I got a *different* error! I took a picture and attached it to this post. As you'll see, it says "Starting up..." then a bunch of gibberish. I'm not sure whether this is a step foreword or not. :P

So, does anyone have any idea how to fix this?

---

### Post by coffeecat on 2008-08-30
You say "Linux works fine." I presume this is on another partition of the same hard disc. If so could this be due to one or more [bad sectors]("http://en.wikipedia.org/wiki/Bad_sector") that are physically within your Windows partition? I would have thought the Windows partitioner on the install disc would have done a chkdsk and found them, but maybe, maybe not. And I would have thought that if the drive is not more than a few years old, the disk controller would have dealt with this.

Nevertheless, why not do a chkdsk of the offending partition from the Windows disc, and/or a 'badblocks' from your Linux install?

---

### Post by King_Critter on 2008-08-30
Hrm. I tried chkdsk, and it said that it had found and fixed one or more errors... but Windows still isn't booting. I even tried installing a diferent version of Windows from a diferent disk, and it still didn't work. Next I'm going to try installing Windows on a diferent hard drive. If *that* doesn't work... well, that would suck.

---

### Post by King_Critter on 2008-08-30
Ok, this sucks. Tried installing it on my other drive, and got the same error. Something is seriously wrong here.

Next I'm going to download VirtualBox and install it on there just to eliminate the possibility that both install disks are corrupted.

---

