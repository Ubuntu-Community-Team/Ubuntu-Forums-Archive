---
title: "Separate windows partition to a new drive"
date: 2014-05-21
forum: Windows
---

### Post by justinr2 on 2014-05-21
I currently have my windows partition living on the same drive as my ubuntu partition.

sda                          107.1G            
&#9500;&#9472;sda1                ntfs     100M            System Reserved
&#9500;&#9472;sda2                ntfs    59.9G            
&#9500;&#9472;sda3                           1K            
&#9500;&#9472;sda5                         1.9G            
&#9474; &#9492;&#9472;cryptswap1 (dm-0) swap     1.9G [SWAP]     
&#9492;&#9472;sda6                ext4    45.2G /          

I would like to move those partitions off to another drive and extend the ubuntu partition to fill the drive. I know I could copy the partition to the drive using dd but what do I need to factor in regarding actually being able to boot to windows?

---

### Post by TheFu on 2014-05-21
If you mirror the drive bit-for-bit (smaller to larger), then Windows will boot and all the current partitions will be the current size.  That would leave lots of empty room after sda6 ... which gparted will easily expand into (if you like). 

Honestly, I'd just create a new partition with whatever amount of storage desired and move my /home into it.  Haven't /home on a different partition than the OS **is** a best practice.

Ok ... so there are some complexities that may or may not matter to you. If the HDD sector sizes between the old and new HDD don't match, you'll want to manually force the alignment and you'll want to be ready with a Windows rescue disk, should that cause issues with booting.

Or ....
you could backup each partition with **fsarchiver**  in turn and manually create partitions on the new HDD. This will definitely break the booting, so be prepared with the Windows rescue disk.

And please, please, please, please make a 100% recoverable backup ****before you start any of this****.  Modifying partitions CAN completely wipe an OS and leave the system unbootable. If there is only 1 PC in the house, it is generally easier to buy 2 HDDs (identical) and mirror them.  That removes the concern over different sector sizes.

---

