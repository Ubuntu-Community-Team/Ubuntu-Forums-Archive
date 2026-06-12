---
title: "Unable to Boot - Kernel Requires ..."
date: 2012-07-09
forum: Ubuntu Studio
---

### Post by hbnmgr on 2012-07-09
Attempting to Upgrade to Ubuntu Studio v12.04 with DVD and get this message.

"This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU."

Have Toshiba Satellite S114.

What does this mean?  Do I have to roll back to previous version? I see other threads on this subject going back for months. Nothing stated on the download page about must have latest CPU with PAE feature. Who would know what that is anyway??? Just wanting to know the latest on this issue as I'm sure everyone else who wants to upgrade their version of Ubuntu.

Thanks!

---

### Post by CrocoDuck on 2012-07-09
Hi, have a look at here: [https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/). It seems that ubuntu 12.04 kernels have PAE enabled by default. Here some suggestion to install ubuntu 12.04 on not PAE capable computers anyway:  [http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p) . If ubuntu studio is what you need, you can always install the packages you need (with mini iso you can do it during installation). Here a guide I found: [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html) .

---

### Post by hbnmgr on 2012-07-09
> **CrocoDuck said:**
> If ubuntu studio is what you need, you can always install the packages you need (with mini iso you can do it during installation). Here a guide I found: [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html) .

Using the above page as a guide, I am stuck here;

PARTITION DISK

Guided Partitioning
Configure Software RAID
Configure the Logical Volume Manager
Configure Encrypted Volumes
Configure iSCSI volumes
#1 Primary      NTFS
#5 Logical  
#6 Logical      NTFS
#7 Logical      SWAP

-----------------------------------

#5 is where I want to install, and was EXT4 until I deleted files on it in a previous step that brought me back to this step.
#1 Has WinXP installed
#6 Has all Backups

What do I select to make my next move of making #5 EXT4 and make it install to that partition?
When I select #5, another page gives the following options;

  Use As:       Do Not Use

  Bootable Flag    Off
  
  Copy Data from another partition
  Erase data on this partition
  Delete the partition
  Done setting up the partition
----------------------------------------------

Yes there are two blank spots selectable but no wording. Previously I chose "Erase Data", now I am back to this or previous screen.
Again - Stuck as to what to select to make it use #5 ???

Thanks!

---

### Post by hbnmgr on 2012-07-09
I seemed to fumble through it by DELETING Partition #5.  It then asked to Format it which is what I wanted it to do and of course it flagged it F and / meaning to format and make root.

---

### Post by hbnmgr on 2012-07-15
Have bigger problems now, after upgrading to 12.04. All screwed up! Upgrade Failed.
Downloaded to Disk - install failed (posted elsewhere) due to CPU needs PAE capability.

Downloaded Mini ISO - install successful, but Pkgs and Updates FAIL.

Will start new thread with all the new problems.

Will this Ubuntu ever get right ???

---

