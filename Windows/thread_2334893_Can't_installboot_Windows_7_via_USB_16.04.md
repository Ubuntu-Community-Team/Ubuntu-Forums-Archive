---
title: "Can't install/boot Windows 7 via USB 16.04"
date: 2016-08-23
forum: Windows
---

### Post by framspace on 2016-08-23
I have the same exact problem (on HP ENVY), unless i'm running only UBUNTU 16.04 LTS and i'm trying to install win7 instead of 8.1 (even if i also had it preinstalled): the install procedure doesn't show up.
I don't know if it can be of any help but in my case if i try to boot from a pen drive nothing happen BUT if i try to boot from the win7 CD then it tells me "press any key to begin installation" but if i press any key it just run Ubuntu normally.
I have already looked around but i found no solution.

EDIT: Just to be more accurate i have already deactivate secure boot and changed the boot order, i've also activeted the legacy mode but nothing worked

---

### Post by oldfred on 2016-08-23
Moved to your own thread as issues are not the same.

Windows only boots from gpt with UEFI.
Windows only boots from MBR with BIOS.

The default DVD for Windows 7 is BIOS boot and then will only install to MBR partitioned drives. Which if drive is gpt, it will erase, but leave backup gpt partition table, seen as corruption drive from Linux view. Can be fixed with fixparts in Linux.

If you have Ubuntu in UEFI mode, best to convert Windows 7 DVD to flash drive and move some files around to make it an UEFI boot/installer. How you boot install media is how it installs.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html
[/URL]
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx) 

If your want the 35 year old BIOS/MBR install, you will have backup all data, install Windows in BIOS mode, and then reinstall Ubuntu in BIOS boot mode.

---

### Post by framspace on 2016-08-23
Thank you for your quick answer but i already have follow the first and the second link before but now thanks to the third i've found a way to find the version of my BIOS/UEFI and it says F.34.
I don't know if i'm right but this could mean that my pc doesn't have uefi but it have bios instead.
If this is right how can i boot win7 from the pen drive? Do i need to use rufus in another way? i just don't know

---

### Post by oldfred on 2016-08-23
I changed title also, I think you can also do that if you edit first post.

I do not have HP, nor know current versions of UEFI from HP. It that the most current version from HP?
And vendors often use same model name for different or updated systems. 

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244) 

 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889) 

 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

