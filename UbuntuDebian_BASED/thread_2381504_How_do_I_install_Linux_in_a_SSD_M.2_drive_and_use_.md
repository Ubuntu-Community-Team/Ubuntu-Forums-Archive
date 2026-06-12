---
title: "How do I install Linux in a SSD M.2 drive and use an SATA HDD for storage?"
date: 2018-01-01
forum: Ubuntu/Debian BASED
---

### Post by maryn2 on 2018-01-01
Hi, I want to install Bodhi in my notebook, but I already have Windows 10 installed on it.

What I want to achieve is a dual booting system with windows 10 (that is already intalled) and Bodhi in a M.2 ssd drive, but I want to keep all the other data in a sata hdd drive that is formated in ntfs.

Can anyone give me detailed explannation on how to do it? What partitions should I create? Do I need a root, home, user, boot, swap partitions? If you have experience on it or have done it before, how would you do it? What is the best way to do it? What drive do I select in "Device For Bootloader Installation"?

I already have a bootable Bodhi USB stick and UEFI options configured.

Any help will be appreciated.

---

### Post by howefield on 2018-01-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2018-01-01
Do not know Bodhi.

Ubuntu's grub only installs grub boot loader with UEFI installs to the ESP - efi system partition on drive seen as sda. So sda must be gpt and have the FAT32 partition with boot flag.

Which drive is sda? Typically, your Windows 10 is UEFI, if pre-installed and will be sda. But some systems my switch drives around when another drive is installs.

Be sure to partition new SSD with gpt and include an ESP, whether That ESP is currently used or not.

Ubuntu now only needs / (root) and ESP if UEFI.
Install of 17.04 or later now use swap file not a swap partition.
You should not need /boot unless running a full drive encryption install which erases entire drive and use LVM which is an advanced volume (partition) system.

I do suggest separate /home if newer user. If very new and just testing Ubuntu you only need /.
But I use data partition(s) as I typically have more than one Ubuntu install and want data mounted in all installs, but not /home as it may be different configuration.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[URL="https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot](http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot) 

[URL="https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

### Post by C.S.Cameron on 2018-01-01
If you want to put your home directory on the HDD, NTFS wont work, you will need an ext partition.
When you boot the Linux OS it should have no problem accessing the NTFS for storage.

---

### Post by maryn2 on 2018-01-08
Ok, I did some research on it and most people add a home partition on the SSD and access the storage drive (the HDD in this case) in NTFS.
My question is, if I do so, if I install Linux programs in a home partition in the SSD will it be installed in the SSD or I can choose to install them in the HDD NTFS drive?
What is the difference between /home and /user partitions?
If I add a home partition in the HDD I will need samba to move archives between OS`s, right?

---

### Post by C.S.Cameron on 2018-01-08
Added programs go into /, not /home. / needs to be on a ext partition and should be on the SSD so the programs start fast

You can put /home on the HDD as this is mostly data, but it needs to go on an ext partition also. 

both Windows and Linux can access the NTFS partition on the HDD.

---

### Post by oldfred on 2018-01-08
Explanation of file structure
[http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/](http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

With Windows 10 you must have its fast start up off if dual booting. It hibernates all NTFS partitions, so then the Linux NTFS driver will not mount any NTFS partition that is hibernated.
       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

