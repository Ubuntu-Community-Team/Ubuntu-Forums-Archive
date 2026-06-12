---
title: "Ubiquity/partman/GRub will not insert proper drive# with multiple hdds"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-04-24
This is probably an old bug.  When installing from USB to hdd on a multi drive system the harddrive # is not correctly recorded in GRUB causing the new install to fail.

  The workaround is that you have to edit GRUB. Find the kernel (which is recorded) then edit and you will find that your secondary hdd is hd0 when it should be hd1. I am really not sure how to flag this one , Ubiquity, partman or GRUB?

---

### Post by oldfred on 2012-04-24
I recently have not had any issues. I installed 12.04 alpha directly from a grub2 loopmount boot of sdb, using the ISO on sda to install to sdd. 

BIOS/grub does always identify the boot drive as hd0 and numbering of fixed drives seems to be in SATA port number. Mixed SATA/PATA systems sometimes have number issues and I did have an issue with an older version, where I installed from one USB flash to another USB flash drive. UUID (in search) was correct, hdX was not but search stopped looking for some reason. After I manually edited the hdX to the correct number then it worked.

I thought the issues of drive numbers changing, particularly removable devices,  was why they changed to UUIDs.

---

### Post by ventrical on 2012-04-24
This is on a Gigabyte MoBo, 2.2 GHz with IDE only. I have the hdds set as master and slave.  There was no problem with previous versions, or precise alpha or beta 1. Just recently with the newer beta 2 and now the pre-release ... it will always write in the slave and hd0 - but it did not do this on previous versions.

  Thanks for your input. I just manually edited it into GRub.

  But I thought it might be important for those running just slightly older machines.

---

