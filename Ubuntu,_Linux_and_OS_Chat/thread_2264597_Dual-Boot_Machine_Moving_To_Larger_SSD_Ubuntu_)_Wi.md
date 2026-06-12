---
title: "Dual-Boot Machine Moving To Larger SSD: Ubuntu :) Win7: X("
date: 2015-02-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Jetjockey on 2015-02-08
Hey guys,
I would very much appreciate if you could help me deal with a Windows 7 issue:
I am trying to clone my 60 GB SSD to a 960 GB SSD, keeping my 2x1 GB Soft-RAID. GRUB and Ubuntu 14.04.1 work straight away, Windows won't move a bit:
1) I've tried dd-ing the entire SSD and also given CloneZilla a few shots.
2) I've tried creating the partition table with the Win 7 install DVD and overwriting the individual partitions.
3) I've tried to simply install Windows on the SSD, while there was only one large NTFS partition.

Neither of these got me anywhere for my ambitions to start Windows, while the first two worked nicely with Ubuntu. I've used boot-repair to find out what is wrong, but cannot read anything from the results:
1) [http://paste.ubuntu.com/10128323/](http://paste.ubuntu.com/10128323/) (Plain copy, three partitions)
2) [http://paste.ubuntu.com/10130074/](http://paste.ubuntu.com/10130074/) (Windows wanted a 100 MB startup partition)

When booting from a 14.04.1 live USB stick, the new SSD seems to alternately show up as sda and sdc. When trying to install Windows on the empty drive, the install fails after the first reboot, as it cannot find a bootable system (blinking cursor), after it has installed the basic files.

What other input do you need to make sense of my case? What else should I try?

Thanks,
Jetjockey

---

### Post by oldfred on 2015-02-08
I do not know RAID nor encryption. 

But Windows needs chkdsk after any resize. And your boot sector info says it was resized as it shows an error. Boot Sector and partition table (fdisk) must have same start & size info. Chkdsk usually fixes that.

---

### Post by Jetjockey on 2015-02-09
Thanks oldfred,
I started the Win 7 install DVD and executed "chkdsk /f c:". However, this did not change the outcome. Today, I also verified that (after a dd from the old to the new SSD) the checksums for the first ~5, ~500, ~36000 MB of the original and new SSD match (dd if=/dev/sdX count=XYZ | md5sum). Any further suggestions?
Thanks,
Jetjockey

---

### Post by oldfred on 2015-02-09
Did chkdsk remove this error?
```

   Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda2 starts at sector 206848. According to the info in 
                       the boot sector, sda2 has 77174783 sectors, but 
                       according to the info from fdisk, it has 1701113855 
                       sectors.
```

If not you may have to use Windows repairs - bootsect.exe:
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


 Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

