---
title: "[SOLVED] Cannot switch back to broken Windows"
date: 2016-04-19
forum: Windows
---

### Post by tri4 on 2016-04-19
Hi,
I'm new to Ubuntu. I have some problem and I need someone to help me on this.
I was using Windows 10 and I installed Ubuntu 14.04 as dual OS with my Windows.
But yesterday, I used Ubuntu and I didn't know my Windows get broken. When I choose to start Windows Boot Manager in grub startup and the screen show me this: 
[IMG]http://www.sevenforums.com/attachments/tutorials/26149d1251766837-dual-boot-installation-windows-7-xp-boot.output.jpg[/IMG]
So now, I don't know how to fix it. I have done what the screen saying, Insert the disk and try to reinstall Windows but I can't. It tells me that the type of disk is gpt.This problem took a day and I need some help!!!!

---

### Post by oldfred on 2016-04-19
If Windows is on gpt partitioned drive it is UEFI boot.
And if you booted Windows installer in BIOS mode it will try to install in BIOS mode and convert from gpt to MBR totally erasing drive. Is that what you want?
Windows only boots in BIOS mode from MBR partitioned drives.

Are you sure you did not change a setting in UEFI?
You may have turned off secure boot in UEFI to install Ubuntu. But you need to keep UEFI boot on.

You should boot directly from UEFI or one time boot key like f10 or f12, not from grub.
Grub only boots working Windows and Windows updates may change settings like fast start up back on, and you need to turn that off. It still should boot from UEFI, but not from grub.

---

### Post by tri4 on 2016-04-19
> **oldfred said:**
> 
And if you booted Windows installer in BIOS mode it will try to install in BIOS mode and convert from gpt to MBR totally erasing drive. Is that what you want?
Yes. That is what I want.

Additional, I don't know what UFEI is. Can you give me more information about this ?

---

### Post by grahammechanical on 2016-04-19
It is called a boot system. In olden days it was a BIOS boot system. BIOS = Basic Input Output System. It was information installed in an integrated circuit that informed the motherboard what kind of computer it was supposed to be. What drives it had. How much memory it had. That sort of thing. It had a settings utility that allowed us users to make certain changes. Such as booting from a CD drive and not the hard drive or which of several hard drives to boot from.

It had its limitations. The top limitation was that it used MBR partitioning which limited the user to 4 primary partitions and we had to use a work around to have more than 4 partitions.

The BIOS boot system has been replaced by UEFI - Unified Extensible Firmware Interface. One of the advantages of UEFI is that it works with GPT partitioning which allows us to have many more than 4 partitions.

It is backwards compatible with MBR partition drives and there is a mode or setting that will allow us to install operating systems that are not written to work with UEFI. This setting is called BIOS/Legacy/CSM mode.

From Windows 8 onwards machines that came pre-installed with Windows had Windows installed in EFI mode. And that meant that any other OS had to be installed in EFI mode as well. If we install Ubuntu in BIOS/Legacy/CSM mode then we can load Ubuntu when the UEFI boot system is set to Legacy mode and we can load Windows 10 when the UEFI boot system is set to EFI mode. But try to load Windows 10 from Ubuntu loading in Legacy mode & things do not work so well.

Just in case you are wondering. Ubuntu can install on machines that have a BIOS boot system or a UEFI boot system and when on a UEFI boot system Ubuntu can be installed in Legacy mode or EFI mode. 

Regards.

---

### Post by oldfred on 2016-04-19
More info if interested. BIOS/MBR is 35 years old and needed updates to work with newer systems,  that it really could not accommodate well.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by RobGoss on 2016-04-19
Here's a bit more info on using UEFI [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Are you also trying to reinstall** Windows 10**? if so how are you going about it did you have a installation disk that came with your machine

---

### Post by tri4 on 2016-04-19
Im trying to reinstall Windows 10. I do have a Windowns 10 installation disk. Please tell me exactly what I have to do.

---

### Post by RobGoss on 2016-04-19
> **tri4 said:**
> Im trying to reinstall Windows 10. I do have a Windowns 10 installation disk. Please tell me exactly what I have to do.


Would you mind telling us how old this machine is?

And what are the specs for it as well this will help us give you the best answers possible

---

### Post by tri4 on 2016-04-19
It's a laptop, Asus ROG G501JW.

---

### Post by oldfred on 2016-04-19
Be sure to boot in UEFI boot mode from UEFI, not BIOS/CSM/Legacy.
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085)

---

### Post by cariboo on 2016-04-20
Not an Ubuntu question, moved

---

### Post by marcinoo on 2016-07-09
lol, welcome to the club, my condolences, check this [http://ubuntuforums.org/showthread.php?t=2329948](http://ubuntuforums.org/showthread.php?t=2329948)

---

