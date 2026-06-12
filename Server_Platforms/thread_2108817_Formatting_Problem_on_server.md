---
title: "Formatting Problem on server"
date: 2013-01-25
forum: Server Platforms
---

### Post by tj107us on 2013-01-25
Hey guys i'm putting together a web file server and when i am trying to install Ubuntu Server 12.04 I get to the partition faze and it shows that the drive i'm trying to install the OS to is only 33.6Mb and not the 16Gb SD card thats in there. I'm using a SD to CF adapter that fits into a CF to IDE adapter. Is this setup limiting my storage space. The computer i'm using is a HP Pavilion 763n desktop.
 
 
Thanks for any and all help you may provide,
tj

---

### Post by tgalati4 on 2013-01-25
When you are in the partitioner, which I assume says:  "GParted (as superuser); you will see a box in the upper right that says:  "/dev/sda"  That is a chooser dialog, use the mouse and change to a different drive.

---

### Post by darkod on 2013-01-25
Does it actually says the disk is 33MB or only that it has 33MB of free unallocated space? If you have partitions on the card they are not considered as available unless you use the manual partitioning method.

Also, the setup you have might be misrepresenting the size. Can you get a CF card and use it with the CF to IDE adapter only? I'm not sure whether it can understand it correctly using two adapters.

Also, I believe the CF cards are better to be used as a disk compared to the SD cards.

---

### Post by tj107us on 2013-01-25
> **darkod said:**
> Does it actually says the disk is 33MB or only that it has 33MB of free unallocated space? If you have partitions on the card they are not considered as available unless you use the manual partitioning method.
 
Also, the setup you have might be misrepresenting the size. Can you get a CF card and use it with the CF to IDE adapter only? I'm not sure whether it can understand it correctly using two adapters.
 
Also, I believe the CF cards are better to be used as a disk compared to the SD cards.
 
 
 
the disk is in one partition formated to FAT32, it wont like me delete the volume in windows disk management. so how do i get it to unafillated space again? Yeah i want to use a regular CF card just dont have the money for one right now and i already had the SD card cause it came with my Canon dslr camera. The adapter was only 15 bucks and free two days shipping with amazon prime. So thats the reason im trying it that way, but if i need to save my money and get a CF card and replace the SD to CF adapter i can.

---

### Post by tgalati4 on 2013-01-25
You can install to FAT32, and that might work better with the SD card anyway.  But I agree, a CF card would probably last longer for this application.  You lose some speed efficiency with FAT32, but because SD cards are slow to begin with, you won't notice it.

---

### Post by cariboo on 2013-01-26
I'm a bit confused here, are you installing the server version with it's text based installer, or are you installing the desktop version, which uses a graphical installer?

If you are using the desktop installer, choose the second option when you get to the partitioning portion of the installation.

If you are doing the text based installation of the server version, it could get a little complicated. Please let us know which you are trying to install.

**Note:** You should be aware that the server version doesn't install a gui desktop by default, so if you aren't comfortable on the command line, the desktop version may be the best for you.

---

### Post by darkod on 2013-01-26
Windows disk management should also allow you to delete the partition, except if windows is running from it at that moment. You can't delete a partition you are running from.

Also, as cariboo mentioned, you can eaither use the whole disk option in the installer or manual partitioning. Both can delete that partition.

> **tgalati4 said:**
> You can install to FAT32,

Are you suggesting he can install ubuntu on fat32? I haven't seen that so far, I don't think it's possible. Unless you are talking about wubi which is not proper ubuntu installation.

It needs a linux filesystem to install.

---

### Post by tj107us on 2013-01-26
> **cariboo907 said:**
> I'm a bit confused here, are you installing the server version with it's text based installer, or are you installing the desktop version, which uses a graphical installer?
 
If you are using the desktop installer, choose the second option when you get to the partitioning portion of the installation.
 
If you are doing the text based installation of the server version, it could get a little complicated. Please let us know which you are trying to install.
 
**Note:** You should be aware that the server version doesn't install a gui desktop by default, so if you aren't comfortable on the command line, the desktop version may be the best for you.
 
 
 
its the server version(text based). I tryied using whole disk, but it say that all data will be deleted and i click ok and then it comes to a red/orangist screen says that there is only 33.6Mb left. I know thats BS cause i found a program (Mini Tool Partition) and deleted the partition on the SD card. I might just need to get a CF card and try that!!
 
 
oh i should menchen that the same 16Gb SD card work on my other computer(one i built), causes i had 64-bit server on it. and was able to boot from the card reader that i install in the front. But i had to delete it so i could install the x86 server version to run on the HP computer. Cuase its only got a older Pentium 4(PGA 478 i think not sure), and not the LGA775 verison of the P4.

---

### Post by tgalati4 on 2013-01-27
Installing to FAT32 would be a form of unetbootin installation, except to an SD card instead of a flash disk.  That requires a FAT32 partition to allow a bootstrap partition, then the rest of the operating system is copied as files, but when run, it is running in RAMdisk using ext4.  So it's a different way of installing, but, in theory it should work.

---

