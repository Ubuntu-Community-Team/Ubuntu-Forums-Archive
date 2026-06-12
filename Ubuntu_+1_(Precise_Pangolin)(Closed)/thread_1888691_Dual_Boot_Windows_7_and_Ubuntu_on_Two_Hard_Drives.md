---
title: "Dual Boot Windows 7 and Ubuntu on Two Hard Drives"
date: 2011-11-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-29
> **smithaaren said:**
> Once installed, load up EasyBCD and select Add New Entry tab. Select the  Linux/BSD, and select GRUB2 from the Type menu. Change the name field  to the edition of Ubuntu you installed, and then select Add Entry.  Select the Edit Boot Menu button to check your results. If everything is  correct, exit out of EasyBCD. Restart your computer and see if Ubuntu  is in the boot menu for Windows 7. If you've followed this guide, then  everything will work perfectly. Congratulations, you now have a system  that can boot both Windows 7 and Ubuntu on two different hard drives!
<snip>

You're kidding.

---

### Post by cariboo on 2011-11-29
> **smithaaren said:**
> Once installed, load up EasyBCD and select Add New Entry tab. Select the  Linux/BSD, and select GRUB2 from the Type menu. Change the name field  to the edition of Ubuntu you installed, and then select Add Entry.  Select the Edit Boot Menu button to check your results. If everything is  correct, exit out of EasyBCD. Restart your computer and see if Ubuntu  is in the boot menu for Windows 7. If you've followed this guide, then  everything will work perfectly. Congratulations, you now have a system  that can boot both Windows 7 and Ubuntu on two different hard drives!
[iphone](http://iphonereleases.com/)

It's way easier just to let grub detect your operating systems. I currently triple boot Precise, Oneiric and Windows 8. I let grub do all the dirty work. :)

Currently the Windows 8 entry says Window Recovery Partition, but I can't be bothered to change it, as I don't boot into Windows often enough to worry about it.

---

### Post by cariboo on 2011-11-29
I didn't notice the spam in the first post :(, now it's gone, so thread closed.

---

