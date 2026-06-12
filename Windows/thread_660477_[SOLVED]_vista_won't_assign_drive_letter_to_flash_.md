---
title: "[SOLVED] vista won't assign drive letter to flash drive"
date: 2008-01-06
forum: Windows
---

### Post by motoperpetuo on 2008-01-06
i've been struggling with this weird problem on my wife's acer laptop with windows vista for months, and wishing there were a good forum like the ubuntu forum, but for vista. then it occured to me that the ubuntu forums have a windows section, so i figured i'd throw it out here to all of you.

basically, if you insert a USB flash drive into my wife's laptop (running vista home premium), vista sees the drive, but won't assign a drive letter. if you go into disk management, the drive is there, but no drive letter. if you try right-clicking on the drive and using the "change drive letter" option to manually assign a drive letter, you get an error that reads that the operation failed.

to add to the weirdness, if i hook up my maxtor external hard drive, vista assigns a drive letter to it and everything works fine. all other usb devices work fine, too. also, i tried booting the laptop into puppy linux, and the flash drive works just fine in it, which i guess eliminates the possibility of a hardware problem.

i tried restoring vista from the restore partition, and interestingly enough, the flash drive works and vista assigns it a drive letter initially. however, after applying windows updates the problem surfaces again: vista again sees the USB flash drive but won't assign a drive letter. same results with any number of flash drives i've tried.

so, i guess it's one of the windows updates that's somehow causing the problem. one of these days when i have several hours, i'll probably try uninstalling the updates one by one until i figure out which one it is, but on the off chance anyone here has heard of this problem, i figured i'd post it here. it's a very slight chance, i think, because i've searched all over the internet and not seen a single reference to this specific problem.

anyway, thanks for your time, everyone!

---

### Post by kamaboko on 2008-01-06
I'm curious, did you ever try to format the flash drive?

---

### Post by motoperpetuo on 2008-03-29
just installed vista service pack one, and it seems to have fixed the problem. vista now assigns a drive letter to any flash drive i try, and i'm able to access files on the flash drive. so, if anyone runs into this problem on vista, try installing SP1.

that said, i'm a little worried that it will break again. i tried reinstalling vista from the restore partition ("restore partition"...is it any wonder i favor linux?) and initially, after the restore, flash drives worked. however, after i applied all the available updates, the problem resurfaced. so, who knows if microsoft will release an update down the road that will break this again?

---

