---
title: "&quot;Boot Device Not Found&quot;"
date: 2015-11-02
forum: Windows
---

### Post by ray9 on 2015-11-02
I have a HP Laptop Pavillion g7.  It had Win 8 on it and I  installed Ubuntu 14.04 on it.  Then I installed a security system in my house that worked with Windows only, so I wiped the disc and was going to install Win 7.  Now I get the "Boot Device Not Found" error.  I have tried everything recommended by HP and every "You Tube" video I could find to fix this with no luck.   When I try to boot from "Laptop Hard drive" I ge this error "error: no such partition, entering rescue mode.....grub rescue>"    So I've come to this forum for a solution.

Thanks

---

### Post by yancek on 2015-11-02
>  So I've come to this forum for a solution.

You've come to the wrong place.  Your question is totally windows and this is a Linux forum.  I would suggest that you post or do a search at a windows forum or the support.microsoft site.  A number of members here are familiar with windows so you might check back if your search doesn't provide resutls.  Some possible problems are that you initially had windows 8 installed and if this was pre-installed, it was likely UEFI rather than MBR.  Windows 7 was MBR by default.

Do you have a windows 7 installation DVD?  When do you get this error?  Is it immediately on booting the computer?  Did you change the BIOS setup so that the DVD drive was set to first boot priority?  Have you tried the windows 7 installation DVD on another computer to see if it boots?  You might need to reset the legacy boot option, see the last post at the HP support page below.

---

### Post by oldfred on 2015-11-02
Moved to Windows sub-forum.

You may have secure boot on. Windows 7 is not secure boot.
Or did you install Windows in BIOS boot mode. Then you have to turn off UEFI boot and turn on BIOS boot.
       Windows Repair Console ------------
f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

    
Windows 7 installer has to be copied to flash drive & some slight reconfiguration to make it an UEFI installer.

---

### Post by ray9 on 2015-11-02
I can't get anything to run, any linux version or win7.

---

### Post by yancek on 2015-11-02
You were asked a number of questions above and didn't answer any of them.

> When I try to boot from "Laptop Hard drive" I ge this error "error: no such partition

You get that error when you try to boot from the hard drive and you said you "wiped the disc".  That would include "wiping" the Grub boot files.  Providing answers to questions previously asked might help.  I forgot to post the link to HP, take a look at the last post on the page and see if that helps.

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Boot-device-not-found-Pavilion-G7/td-p/2283435](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Boot-device-not-found-Pavilion-G7/td-p/2283435)

---

### Post by ray9 on 2015-11-04
> **yancek said:**
> You've come to the wrong place.  Your question is totally windows and this is a Linux forum.  I would suggest that you post or do a search at a windows forum or the support.microsoft site.  A number of members here are familiar with windows so you might check back if your search doesn't provide resutls.  Some possible problems are that you initially had windows 8 installed and if this was pre-installed, it was likely UEFI rather than MBR.  Windows 7 was MBR by default.

Do you have a windows 7 installation DVD?  When do you get this error?  Is it immediately on booting the computer?  Did you change the BIOS setup so that the DVD drive was set to first boot priority?  Have you tried the windows 7 installation DVD on another computer to see if it boots?  You might need to reset the legacy boot option, see the last post at the HP support page below.

Yes I have the Win7 DVD.  I get the error when starting the laptop.  Yes the error shows immediately.  Not sure about boot priority.  No I haven't tried the dvd on another computer, but have used it to install on another computer.

So I got win7 to load,  and partially install but it stops at the windows screen.  I did wipe the grub files.

---

### Post by yancek on 2015-11-04
Did you try the option at the HP forums at the link I posted previously?
Did you check the BIOS to see if UEFI was enabled/disabled?
Have you reviewed the links posted by oldfred above?

Are you not able to start the install of windows 7?  Never installed it myself so I don't know what one would expect?

---

### Post by ray9 on 2015-11-07
Yes,  yes and yes.  It boots win7 to the "Starting Windows" screen and freezes.  I'm not getting the screen to "Repair computer" anymore.

---

### Post by oldfred on 2015-11-08
If system was originally Windows 8, then it was UEFI with gpt partitioning. Ubuntu probably was installed to gpt partitioned drive as it can use gpt with either UEFI or BIOS boot.

But Windows 7 DVD only installs to BIOS and will not install to gpt. If hardware is UEFI, probably better to convert Windows 7 DVD to flash drive and make changes to allow it to install in UEFI mode.

 Identify if system is UEFI or BIOS
[http://www.rodsbooks.com/refind/bootmode.html#windows](http://www.rodsbooks.com/refind/bootmode.html#windows)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by ray9 on 2015-11-08
It boots, it just won't install.  Thanks.

---

### Post by yancek on 2015-11-08
If the windows 7 DVD is booting to "Starting Windows" and won't continue, you might try googling that error message or posting at a windows forum.

---

