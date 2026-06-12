---
title: "Installing Bodhi Linux on a 32-bit Apple laptop"
date: 2017-01-28
forum: Ubuntu/Debian BASED
---

### Post by g33zr on 2017-01-28
Try Bodhi Linux, which still supports 32-bit.

---

### Post by joannacw on 2017-01-31
Thanks! [FONT=Helvetica Neue]I just downloaded the 32bit AppPack release, and burned the .iso file to a DVD. (I don't have a large thumb drive free.)  I booted to the DVD and got a black screen with this message in white:

[/FONT][FONT=Helvetica Neue]1.
[/FONT][FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]2.[/FONT]
[FONT=Helvetica Neue]Select CD-ROM Boot Type:

Hitting 'enter," typing 'live' and typing 'efi' all have no effect--no type appears and the screen doesn't change.

Is there a disc error? Or is there something else I should type? Is there a quick-start guide for testing/installing Bodhi from a DVD? I've not gotten this question when trying to install Xubuntu or Lubuntu from live DVDs. (I have a [/FONT][COLOR=#000000][COLOR=#000000]M[/COLOR][/COLOR]*acBook Pro 1,2 with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM)*[FONT=Helvetica Neue]

Any advice greatly appreciated.[/FONT]

---

### Post by g33zr on 2017-01-31
Did you try installing Bodhi in a virtual machine first? If so, how did it work for you? 

Did you burn the ISO onto a CD or DVD? In either case, it should have booted with a menu allowing to either run it live or install. I'm not sure what's going on with your laptop. Maybe it's time to replace it because fewer distros are providing 32-bit support.

---

### Post by joannacw on 2017-01-31
No, I haven't yet learned to run virtual machines.

I burned the ISO onto a DVD.

---

### Post by g33zr on 2017-01-31
I'm not sure what you've read online about installing Linux, so allow me to recommend some reading.

I trust you downloaded the correct ISO from Bodhi. Have you checked the Bodhi forum to check if other MacBook users have similar problems? Did you hold down the C key when booting the DVD? (Once you install Bodhi, you would hold the option key to boot.)

If you plan to dual-boot and use rEFInd: [http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html) Some of the info on these Ubuntu links are dated (i.e. rEFIt), but there are some good tips: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) and [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Good luck!

---

### Post by g33zr on 2017-02-02
@ Joanna: Which version of MacOS are you running on your laptop? I suspect that you might be having a problem with whichever software you're using to burn the ISO onto a DVD. I recommend you try a different method of burning your ISO. Try installing and running [Etcher]("https://etcher.io"), which is cross platform and allows you to create a bootable ISO on a SD card or USB stick in three easy steps. But, if you prefer to burn your ISO on a DVD, there are plenty of free cross-platform options out there.

---

