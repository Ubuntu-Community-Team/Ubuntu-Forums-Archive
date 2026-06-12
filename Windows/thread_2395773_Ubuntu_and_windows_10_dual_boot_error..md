---
title: "Ubuntu and windows 10 dual boot error."
date: 2018-07-06
forum: Windows
---

### Post by Oreo100 on 2018-07-06
I have been attempting to dual boot my dell xps 15 9570 with ubuntu. I turned off fastboot and changed raid on to ahci. I had the latest version of ubuntu loaded onto my usb flash drive and I tried to install it. The first problem I had was when trying to install ubuntu the screen froze and i could go no further. I got past this by updating my bios and switching from raid on to ahci. However after i managed to install ubuntu windows would not start and it kept looping around to the automatic repair tool. Also after restarting my computer after installing ubuntu and returning to try and log in it would freeze after i logged in. So in my case neither of the operating systems were working. I decided to give up on ubuntu and try to fix windows. Upon removing my usb device the grub disappeared and i was just left with windows. However it was still stuck in this loop. I tried changing the secure boot setting in the bios however this did not work. I ended up attempting to return the computer to factory settings however windows will not boot and it still stuck in this boot loop. Any help with either os will be greatly appreciated. I am very up at the minute as I have just bought this laptop for college which starts in two months and i will be in big trouble if I cannot manage to fix it.

---

### Post by Oreo100 on 2018-07-06
I am also afraid that I have removed the windows operating system from this computer and I am wondering how can I put it back on.

---

### Post by oldfred on 2018-07-06
You have to install AHCI drivers into Windows before changing from RAID to AHCI. Or boot into recovery mode directly from UEFI and maybe f8 still works to get into Windows repair mode?
You may be able to reset to RAID and then install AHCI  drivers also.

If you erased Windows, did you erase backup partitions. Or make the Windows backups.
My Dell wanted both Dell full backup and Windows backup and I did a full image backup using Macrium Reflect. Multiple flash drives & DVDs. 

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Oreo100 on 2018-07-06
It looks like I have erased all partitions and backups. Will I have to reinstall windows 10 again? If so how would I go about doing this and will I have to pay for another version? I im going to give up on trying to dual boot with ubuntu for the time being.

---

### Post by oldfred on 2018-07-06
Since now just Windows, moved to Windows sub-forum.

If newer system with UEFI, Microsoft records your product key in the UEFI. Will not work with BIOS install.
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key) 
    
But Dell has many drivers, best to install Dell OEM copy. Not sure if Dell has that directly available or not. Some vendors let you download it, some charge, and some offer nothing.
Microsoft has generic Windows, which will work for a short time before it requires product key. It may see Dell key you have? But it may be difficult to install without Dell's drivers.
Best to contact Dell.

---

### Post by Oreo100 on 2018-07-06
What should I do?

---

### Post by oldfred on 2018-07-06
Did you contact Dell?

---

