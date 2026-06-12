---
title: "Guide: Software raid and LVM full disk encryption - Oneiric 11.10"
date: 2012-03-04
forum: Tutorials
---

### Post by EtoIxPi on 2012-03-04
(Pictures to come later)    I'm writing this because I couldn't find any guidance when I searched and I don't want you to waste your Saturday morning like I did. ;)    

This brief guide assumes that you will be installing Ubuntu as your only operating system, I am not sure if you could get the software raid to work with a dual boot setup.    

Step 1: Download the alternate install image.  
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.10/release/)    

Step 2: Go through the normal setup steps, stop when you get to the partitioning screen.    

Step 3: Select 'manual'.    

Step 4: Remove all partitions. 

   Step 5. Create a 550MB /boot partition on one of the drives. Set the format to be ext4.    

Step 6. Select 'Configure software raid' and add the select the free space left over that you'd like to include in your raid setup.     

Step 7. Select your raid configuration. I picked raid0.  

Step 8. After you're finished with raid select 'Configure encrypted volumes'.     

Step 9. Encrypt the raid partition and hit finish. It will now ask you to choose a pass phrase.   

Step 10. Activate the raid partition.    

Step 11. Create a LVM on the encrypted partition.  

Step 12. Create / and swap on the LVM.    

Step 13. Install!    

Step 14. You'll have to install grub to the one of the hard drives. Put it on the same one as the /boot partition and set your bios to boot that drive.

---

### Post by BBUCommander on 2012-05-30
I followed this guide in Ubuntu 12.04 and it worked like a charm.  Thank you very much for putting this together!  You save me countless hours of frustration figuring this out on my own.

---

### Post by kevashcraft on 2013-05-02
Many many thanks!!

Just used this method to create a RAID1 Encrypted LVM on Ubuntu Server 13.04! :guitar:

Note: There was not an "activate raid" option, it appears to have been activated when originally created?

---

### Post by ITfromScratch on 2013-07-17
Is this creating a boot partition on only one of the drives? 

If you want to create a RAID1, how could you create a boot partition on the second drive also?

---

