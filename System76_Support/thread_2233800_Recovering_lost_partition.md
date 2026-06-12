---
title: "Recovering lost partition"
date: 2014-07-10
forum: System76 Support
---

### Post by chrismamo1 on 2014-07-10
Hi, I recently ran into a spot of trouble with my Bonx7. While using the device normally, the hard drive started making interesting noises, so I immediately shut down the device. The device no longer reads my second hard drive at all, and will no longer boot into the installation I was using at the time (this installation lives on a second partition immediately following the installation that came with the device and immediately preceding the swap partition). Live disks seem to work, though, and I am able to read from the old partition just fine. However, the main partition I was using does not appear to be in the partition table anymore, and testdisk cannot find it. I believe that this May be due to my decision to encrypt the drive during installation of Ubuntu. Is it possible to add the partition to the partition table without over writing anything? I know the exact sectors where the partition should begin and end, and I have the decryption key.

thanks,


Joh Christopher McAlpine

---

### Post by oldfred on 2014-07-11
Is it MBR or gpt partitioned?
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Parts.txt is just a text file and can be manually edited if you know exact start and size (not end).

You may also be able to use parted rescue as you have to tell it approx. start & end.

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

      
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by chrismamo1 on 2014-07-11
Thank you very much for the response. I tried using "sfdisk -d" on a clone drive I created, but was met with a warning that sfdisk does not support GPT, and that I should use Parted instead. I have attempted to use the rescue function in Parted, but to no avail. Does Parted allow the manual editing of partition tables through text files, or is there some other tool that may be used with GPT?

Also, I backed up the 750GB disk (/dev/sda) onto a 1.5TB external hard drive (/dev/sdb) with the command "dd if=/dev/sda of=/dev/sdb". The partition structures seem to be identical (except for all of the extraneous space at the end of the external hard drive), but I have no way of telling whether the information in the I allocated space (the information I'm trying to save) was actually transferred. Does the dd command do this automatically, or is there any other way to check?

thanks,


John Christopher McAlpine

---

### Post by oldfred on 2014-07-11
If a gpt drive  you have to use gdisk. The gpt partition table does have a backup which may save you?

 Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

   sudo apt-get install gdisk
sudo gdisk /dev/sda
Command (? for help): 

   More info:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

I have also seen where drive had overlap to end. And the suggestion was to delete partition and then just recreate with correct settings. If partition is totally missing you may be able to just add it. Do not reformat, just create a new partition table entry that exactly matches old start, size/end must be close or if data near end it may get corrupted.

---

