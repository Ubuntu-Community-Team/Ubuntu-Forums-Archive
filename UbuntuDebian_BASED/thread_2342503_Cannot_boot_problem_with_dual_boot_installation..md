---
title: "Cannot boot problem with dual boot installation."
date: 2016-11-07
forum: Ubuntu/Debian BASED
---

### Post by mrjimascroft on 2016-11-07
[COLOR=#000000][FONT=Open Sans]I have an issue with a two ssd system one had Windows 10 and one Elementary Linux.[/FONT][/COLOR][COLOR=#000000][FONT=Open Sans]I think the windows ssd was preventing elementary booting and so I  removed it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]Now I have one with deepin and one withe elementary.[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]I have run boot repair but I still cannot boot into elementary.

The pastebin output from boot repair is below.[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]http://paste2.org/6zbKZxNX
[/FONT][/COLOR]
also I ran update grub and got this:

 Generating grub configuration file ...Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found Deepin 15.2  (15.2) on /dev/sda1
Found elementary OS 0.4 Loki (0.4) on /dev/sdb1
done


[COLOR=#000000][FONT=Open Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]Any insight would be much appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]Thanks[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Open Sans]Jim[/FONT][/COLOR]

---

### Post by oldfred on 2016-11-07
Moved to Other OS sub-forum.

Which drive are you booting from and which install does not work? You show two elementary, sdb & sdd (external).

Did you reformat a drive. 
One version of boot stanza shows gpt partitioning. But drives seem to all be MBR(msdos) partitioned now.
So old entries using UUID will not work if reformatted.

Best to keep all drives in drive order. I found issues when drives changed boot order, even though they should be booting by UUID.

You should system hardware is UEFI. Is Windows install UEFI and everything else BIOS?
I started converting all drives to gpt back with 10.10? And when Windows 8 came out & all new systems were UEFI/gpt, I started to include both ESP & bios_grub on every drive, so when I got a new UEFI based system, I could easily convert drive from BIOS to UEFI.

Do not use Boot-Repair's default repair with multiple drives & installs. Always use advanced option and choose each install and then same drive for that install's boot loader. Then from UEFI/BIOS you should be able to directly boot any install using that drive's MBR.
 
And with multiple installs, keeping the one main working install updated can be a bit of a hassle. I have many Ubuntu install, so I turn off os-prober and add my own boot stanzas to 40_custom and boot partition, not specific kernel.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by mrjimascroft on 2016-11-11
Thank you very much for your comprehensive reply.
[COLOR=#000000]"One version of boot stanza shows gpt partitioning. But drives seem to all be MBR(msdos) partitioned now."
[/COLOR]I had thought the OS install took care of the best formatting of the drives etc during installation. Not sure where the MSDos came from.

I eventually reinstalled elementary linux on one ssd alongside deepin on the second ssd. Windows 10 is now isolated in its own PC!
I tried boot repair on the elementary SSD but it would not let me change the default OS it just stated that this option was only available from a live boot cd.
It would be great to have a blog post for dual ssd dual os linux systems if anyone knows about one specifically on this?

---

### Post by oldfred on 2016-11-11
Does not matter that it is dual SSD, or just two drives or even full installs to an external drive, flash or hard drive.
But it does matter if UEFI or BIOS.
I have multiple installs on multiple drives, back when I had BIOS only, and now with UEFI. And UEFI is more complex.

But in all cases better to partition in advance, use Something Else to install.
       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/) 
    
I do add my own boot stanza to 40_custom. Otherwise difficult to keep track of grub entries and updates.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

I also share data partition(s). Back when still using XP, I had both a shared NTFS and a Linux formatted data partition.
That was so all data that I might want when booting any install was there.

---

