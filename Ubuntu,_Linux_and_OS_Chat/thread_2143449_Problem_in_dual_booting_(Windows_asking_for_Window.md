---
title: "Problem in dual booting (Windows asking for Windows)"
date: 2013-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by c2tarun on 2013-05-09
Hi friends,

I purchased Iphone5 and thanks to apple I have to dual boot my system. I have 5 partitions in my system. The smallest partition which I don't use is of 5GB (I keep it for testing other linux distros) Now I want to install Windows XP in there. I made a bootable pendrive of WinXP and tried to boot using that pendrive. It booted successfully but I got a message something like this:

```
No Windows installation can be detected. Please insert Windows 2000/ME/XP/2003 installation disc.
```

Any suggestions what can I do?

Note: I have all the partitions in ext4 format. I just thought about it, could this be the reason? I'll go home and test it today, but it'll be great if anyone can confirm this. I thought that I'll format that partition. to FAT or NTFS during installation.

---

### Post by oldfred on 2013-05-09
Windows only installs to primary (sda1 thru sda4) partitions formatted NTFS with the boot flag. Is 5GB enough?
Also some have had issues if the primary partition used for the install is after the primary partition used as the extended. Windows does not see ext4 partitions and sometimes does not rewrite partition table correctly. It installs its boot loader and may rewrite partition table.

       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

      
 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by Bucky Ball on 2013-05-09
*Thread moved to **Ubuntu, Linux and OS Chat***

---

### Post by c2tarun on 2013-05-10
> **oldfred said:**
> Windows only installs to primary (sda1 thru sda4) partitions formatted NTFS with the boot flag. Is 5GB enough?
Also some have had issues if the primary partition used for the install is after the primary partition used as the extended. Windows does not see ext4 partitions and sometimes does not rewrite partition table correctly. It installs its boot loader and may rewrite partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2


Thanks for replying, I figured that I have to install Windows to sda1 :( That crap required more than 12GB for installation. And after that much no sound driver, graphics driver, LAN driver or wifi driver. I have to download evey driver.

Anyway, I'll still use Ubuntu as my primary OS, will installing Ubuntu in some other partition will cause some performance issue? Also now is it possible for me to install WinXP in a small 5GB partition and then remove Win7 and install Ubuntu in /dev/sda1.

---

### Post by oldfred on 2013-05-10
If dual booting you will have no performance issues. Some boot with Ubuntu and install XP in virtual install and then it may run a bit slower. For most applications that would not matter, but for games it might. Best to have a lot of RAM as you have to share some of it for a virtual install.

If you have multiple Windows installs on one system you have to be careful on where boot files are. Windows can only boot from one Windows install and second installs copy their boot files into the first install or active partition that we see as having boot flag. Second install has no boot files, but if a primary partition can be repaired to boot on its own.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by MadmanRB on 2013-05-10
> **c2tarun said:**
> Thanks for replying, I figured that I have to install Windows to sda1 :( That crap required more than 12GB for installation. And after that much no sound driver, graphics driver, LAN driver or wifi driver. I have to download evey driver.

Anyway, I'll still use Ubuntu as my primary OS, will installing Ubuntu in some other partition will cause some performance issue? Also now is it possible for me to install WinXP in a small 5GB partition and then remove Win7 and install Ubuntu in /dev/sda1.

Yeah its possible to install winXP but why bother?
Its number will be up next year.

---

### Post by c2tarun on 2013-05-10
> **oldfred said:**
> If dual booting you will have no performance issues. Some boot with Ubuntu and install XP in virtual install and then it may run a bit slower. For most applications that would not matter, but for games it might. Best to have a lot of RAM as you have to share some of it for a virtual install.

If you have multiple Windows installs on one system you have to be careful on where boot files are. Windows can only boot from one Windows install and second installs copy their boot files into the first install or active partition that we see as having boot flag. Second install has no boot files, but if a primary partition can be repaired to boot on its own.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Thanks for the wonderful link :) gave answers to lot of my questions.

> **MadmanRB said:**
> Yeah its possible to install winXP but why bother?
Its number will be up next year.

Yeah I also thought that :P Installing XP will waste another 1 hr of my life. And all I have to do is sync music in iphone. May be counterstrike some day :) but that'll require installing many drivers (and I am too lazy for that).

Thanks a lot for helping guys, I am marking this thread solved.

---

