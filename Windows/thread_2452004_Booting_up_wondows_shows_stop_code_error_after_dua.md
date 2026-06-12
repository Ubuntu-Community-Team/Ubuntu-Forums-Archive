---
title: "Booting up wondows shows stop code error after dual booting with ubuntu"
date: 2020-10-14
forum: Windows
---

### Post by krush11 on 2020-10-14
I have recently dual booted ubuntu. Now i cant load windows. I have tried one solution by going to this : [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Here are the results i got after following the steps
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1   34C8-30D9                              vfat       ESP
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3   6216C93C16C911C9                       ntfs       Krushnal
/dev/nvme0n1p4   DABAC9B0BAC98A09                       ntfs       Recovery
/dev/nvme0n1p5   ce578264-5bc1-4671-bcb6-b46b19070295   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/nvme0n1p1   /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p5   /                        ext4       (rw,relatime,errors=remount-ro)



```

Please help me.

---

### Post by CelticWarrior on 2020-10-14
```
[COLOR=#000000][FONT=&quot]/dev/nvme0n1p1   34C8-30D9                              vfat       ESP[/FONT][/COLOR]


```

This shows the system is UEFI. How were both OSes installed? They need to be in the same mode. If your Windows is preinstalled then it certainly is in UEFI mode. Ubuntu must then be installed in the same mode.

Can you boot Windows directly? Open UEFI settings > Boot and select "Windows bootloader manager" as the frist option. Please report beack, we troubleshoot from there.

---

### Post by krush11 on 2020-10-15
Yes after putting windows on top i am directly able to load windows without grub pooping up.


Here are some settings that i changed which might help you get an insight:
- for grub to open i had to changed the SATA operation mode from Raid to AHCI
- now i was able to start grub and boot ubuntu but whenever i clicked windows in the grub bootloader i found a Stop Code: INACCESSIBLE BOOT DEVICE error message
- after being unable to boot windows i changed it back to raid which helped me regain windows but now i am unable to access ubuntu as grub loader doesn't start

---

### Post by CelticWarrior on 2020-10-15
You need to install AHCI support in Windows then change the mode to AHCI.
Only then the dual-boot will work.

There are literally thousands of threads about the same thing.

---

### Post by oldfred on 2020-10-15
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Grub also only boots working Windows.
Or you have to have Windows fast start up off, hibernation off. 
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Be sure to have good backups and make a Windows repair & recovery flash drive.

---

