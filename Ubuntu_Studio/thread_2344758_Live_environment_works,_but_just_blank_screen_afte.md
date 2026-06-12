---
title: "Live environment works, but just blank screen after install"
date: 2016-11-28
forum: Ubuntu Studio
---

### Post by wookieesa on 2016-11-28
[COLOR=#4D4D4D][FONT=&amp]Hi All

I have an Asus S300CA-C1004H VivoBook:
[/FONT][/COLOR]
[LIST]
[*][COLOR=#4D4D4D][FONT=&amp]i3 CPU
[/FONT][/COLOR]
[*][COLOR=#4D4D4D][FONT=&amp]4GB RAM
[/FONT][/COLOR]
[*][COLOR=#4D4D4D][FONT=&amp]500GB HDD
[/FONT][/COLOR]
[*][COLOR=#4D4D4D][FONT=&amp]Integrated Intel Graphics
[/FONT][/COLOR]
[/LIST]
[COLOR=#4D4D4D][FONT=&amp]
I've had the machine since July 2013 and I've been Running Ubuntu (Alternating between stock Ubuntu & Ubuntu Gnome at various points) on it since then. Recently Ive been keen to test out Ubuntu Studio. 

I have downloaded the Ubuntu Studio ISO (16.10 x64) and created a bootable flash drive, via the universal usb installer. I can boot from the flash drive without issue and as far as I can tell the live environment is fully functional. I test ran it for a good 3 hours using various apps on the system. From the live environment I have run the installer, which completes successfully and I then reboot the machine.

After the reboot I get to a GRUB screen where I can choose either a standard or low latency kernal, aftem making the selection or letting it time out and auto select, the system just goes to a blank screen. Mostly it'll just stay at the blank screen, but a few times it will eventually crash to a busybox shell prompting for [COLOR=#111111][FONT=Consolas](initramfs).

Looking through various forum posts I have tried the folloing:
[/FONT][/COLOR]

[LIST]
[*]Pressing e at grub and adding nomodeset
[*]pressing e at grub and setting different resolutions and the vesa driver
[*]the (initramfs) error advised fixing corruption on the file system, which I have attempted, but fsck reports the file system as clean.
[*]I have repeated the Installation (Fully formatting the drive each try) multiple times, both with and without lvm.
[*]I have tried the install with CSM enabled and Disabled in the BIOS, to try both UEFI and Legacy installs
[*]The downloaded ISO hash was checked, redownloaded anyway to be safe and the flash drive was recreated.
[*]Various reinstalls were attempted with Updated & 3rd Party sotware enabled and disabled in different combinations
[/LIST]
Most given solutions I see for such problems are relating to driver issues, specifically nVidia. The laptop just has generic integrated Intel graphics, but surely if it was driver related the same issue would persist in the live environment ? Further when in the live environment I run the additional drivers tool, and no graphics cards pick up as needing 3rd party drivers.

Some of the forum posts I've looked through for reference:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
[http://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen](http://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen)
[http://askubuntu.com/questions/702279/ubuntu-server-14-04-lts-black-screen-after-grub](http://askubuntu.com/questions/702279/ubuntu-server-14-04-lts-black-screen-after-grub)
[https://community.linuxmint.com/tutorial/view/842](https://community.linuxmint.com/tutorial/view/842)
[https://ubuntuforums.org/showthread.php?t=2209117](https://ubuntuforums.org/showthread.php?t=2209117)
[http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)
[http://askubuntu.com/questions/693683/how-to-fix-the-error-warning-failed-to-connect-to-lvmetad-falling-back-to-intern](http://askubuntu.com/questions/693683/how-to-fix-the-error-warning-failed-to-connect-to-lvmetad-falling-back-to-intern)


[/FONT][/COLOR]

---

### Post by wookieesa on 2016-12-01
I wasn't able to resolve the issue directly, but by formatting and installing an older version of Ubuntu Studio, I have gotten the system functional.

---

