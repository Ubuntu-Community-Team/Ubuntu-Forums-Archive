---
title: "Dualbooting 16.04 and 16.10"
date: 2016-06-03
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-06-03
I decided to install a new 16.04 on some free space on my main drive. Which I am now updating to 16.10. The problem is there's no choice NOT to install a bootloader in the ubuntu installation. So i choose to install it on my USB stick thinking it would fail and I would just do a grub-update form my current 16.04, Well, NO! It magically installed on /dev/sda.

My assumption is that the next time either of the installs update the kernel they would "take" over the bootloader. (Everything works though). But to remove my confusion as to what system I'm booting i would like for one to have complete control of the boot manager. Am I correct in assuming if I remove the grub package from one of them they would no longer be able to or try to update?
----------------------------------------------------------------------------------------------------------------------------------
Well, I assumed  wrong. 

To take back control i had to do a "grub-install /dev/sda" on my 16.04. (However I'll move it back to 16.10 as I rarely update the kernel for 16.04 as it is custom).
The positive is that each distro can live none the wiser ;).

---

### Post by oldfred on 2016-06-03
I have this in my notes, not sure if still valid or not, never used it.
 sudo ubiquity -b
In that case you are able to install Ubuntu without the bootloader. 

Grub does remember where it installed with BIOS installs. 
You may want to check 2nd install and correct it or on some update it will take over again.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    
      
 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

With UEFI, the only real difference with 2nd install is the tiny 3 line grub.cfg that is a configfile to UUID & partition with rest of grub in the ESP - efi system partition.
I just back up my ESP and save the grub.cfg or now know what to edit to restore correct version in boot.

---

### Post by izznogooood on 2016-06-04
The explanation is in the first post. I fumbled upon the solution and answered in another post but the admin merged them (Understandably). So this became a one-post topic.

---

