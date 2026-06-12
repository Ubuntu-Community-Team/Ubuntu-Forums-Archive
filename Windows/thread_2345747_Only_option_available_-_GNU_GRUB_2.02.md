---
title: "Only option available - GNU GRUB 2.02"
date: 2016-12-07
forum: Windows
---

### Post by rpikado on 2016-12-07
Hello everyone,

I am trying to format my laptop with windows 7. I have both Windows and Freya OS installed on my laptop but they are both broken, none of them initializes. Windows gets stuck in start screen, safe mode does not work. The same goes for Freya OS.

The only thing I can access is GRUB 2.02, but i cannot initialize the windows DVD. Is is possible to launch it from the GRUB console? If yes, how?

Thank you very much!

---

### Post by coffeecat on 2016-12-07
Since this is about installing Windows, I've moved this thread to the **Windows** sub-forum.

I think you need to look at your BIOS settings if you want to boot from the Windows DVD. Trying to get the Windows DVD booted from grub would be somewhere between unrewarding to impossible, I would guess, but someone else with more experience of that may be able to comment.

By the way, the General Help section you posted in is for support for the [recognised Ubuntu flavours](https://www.ubuntu.com/download/ubuntu-flavours) only. Elementary OS is not one of them. If you need help with Elementary, you are welcome to post in [this section](https://ubuntuforums.org/forumdisplay.php?f=452), but please be aware that our primary focus in this forum is for Ubuntu itself and the recognised flavours.

---

### Post by yancek on 2016-12-07
>  Is is possible to launch it from the GRUB console? 

No.  If you cannot boot the commercial windows product on the DVD, either you aren't setting the DVD to first boot priority, you have a motherboard/firmware or other hardware problem or the install DVD is bad.

If you can access Grub, you could boot the extracted/copied windows DVD to an ntfs partition and boot from there and install to another partition.  You don't give details on whether you can access Grub or if you have some way to copy the windows DVD contents to the hard drive or a flash drive?

---

### Post by rpikado on 2016-12-08
Hello again and thank you for your answers so far.

I've tried to boot windows from an USB stick but the BIOS does not recognize it. If I have a FAT32 bootable pen it recognizes, but I am only able to make a bootable usb in NTFS, I don't know why but Rufus won't allow me to do int in FAT32 and Microsoft USB Tool neither. I've tried to change it from UEFI to CSM and had to open the computer and reset the motherboard because the screen went all black.

The boot order is fine when I use either CD or USB, I keep changing it according to what I am trying. Given this, I've tried the windows 7 DVD but instead of popping something around the DVD content it jumps straight to a GRUB menu from where I can select elementary OS, System Setup which takes me to BIOS, "e" to edit and "c" to launch the console. This it the only configurable thing I have access apart from the BIOS.

I hope I was more clear this time :)

EDIT: Everything started after I've started getting atikmpag.sys blue screens in Windows 10 related to the graphics card. I've tried 5 minutes ago to install ubuntu, it gets into the purple screen "loading" and then everything goes in some weird colors and the PC freezes. Can this be related in any way to drivers or is my graphics card dead? Also, is there a way to install ubuntu without resorting to the graphics card? Many thanks guys :)

---

