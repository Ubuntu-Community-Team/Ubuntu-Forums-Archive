---
title: "Burg don't find Windows 8.1"
date: 2014-07-20
forum: Windows
---

### Post by ihavenokia on 2014-07-20
Hello, GRUB was not working so i installed burg but after i update burg there is no entry for windows 8.1, only appear ubuntu (twice :S) how can i add windows 8.1 to the list? Thank you

---

### Post by slooksterpsv on 2014-07-20
What is the output of your GRUB, and **most importantly** does your system use EFI/UEFI? If it does GRUB and BURG **will not** pick up Windows 8 and UEFI is handled by the BIOS (well it's its own system technically). If GRUB wasn't working, BURG won't either, BURG uses GRUB. It's justa graphical end for GRUB.

---

### Post by ihavenokia on 2014-07-20
Well...what is EFI/UEFI? i jusr reinstaller grub and the same problem (no win8). I only got ubuntu and mem test. My windows 8.1 is in partition 5 (i checked in gparted). I added 
menuentry "Windows 8" {
    set root='(hd0,gpt5)'
    chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}

but it says that there is not such partition. Help please, it is not mine notebook :S Thank you.

---

### Post by slooksterpsv on 2014-07-20
It is EFI, I'm finding that it most likely won't work. What about rEFInd - [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by oldfred on 2014-07-21
If Windows 8 was preinstalled then you must install Ubuntu in UEFI mode.
UEFI and BIOS are not compatible and once you start booting in one mode you cannot switch (rEFInd may be exception as to how it manages things). 
Or from grub menu you cannot boot any system not installed in same boot mode.
New systems have this for BIOS compatiblity if you want to boot an old hard drive:
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But now Ubuntu live installer will install in either UEFI or CSM mode. But it installs in the mode you select when you boot installer.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Lots more info & useful links in the link below in my signature.

---

### Post by ihavenokia on 2014-07-21
i uninstaller ubuntu and instaled another windows 8.1, but there i have not option to boot my old windows :( what this can be? i don't know what to do :s

---

### Post by yancek on 2014-07-21
Did you have an option with your windows 8 installer to specifically select a partition on which to install windows 8?  Did you get any output when reinstalling windows 8 indicating it had detected a current windows OS on the computer?  I'm not familiar with windows 8 but I expect you have overwritten your original windows 8.  Can you post some output from windows showing your partitions, a disk management tool?

---

### Post by oldfred on 2014-07-21
Moved to other OS since now just Windows.

Did you install your new Windows in BIOS mode or UEFI mode? 
Again UEFI and BIOS are not compatible and if you forced a BIOS install it damaged the UEFI install as it converts drive from gpt partitioning to MBR(msdos) partitioning. You may not even have old install. 

If installed in UEFI mode it may not find the other install if hibernated. Dual boot requires that you turn off fast boot or always on hibernation even if dual booting two Windows.

We only know some info on Windows 8 from those who dual boot, but those that really know Windows are in Windows forums.

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by slooksterpsv on 2014-07-22
ihavenokia - you'll need to boot from a Windows 8 DVD and recreate the EFI boot entry for your other Windows 8 install, see this link:
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

---

### Post by ihavenokia on 2014-07-24
Thank you for the answers, but anyone worked for me so i just uninstalled Ubuntu and Win8 and installed only Win...This is sad cuz i like ubuntu (i am usit it right now) but im not an expert in this so i gave up xD

---

