---
title: "RCA Cambio Tablet W101v2 Hardware configuration Zesty Alpha linuxium relesae"
date: 2017-01-16
forum: Ubuntu/Debian BASED
---

### Post by elizabeth1701 on 2017-01-16
I'm not all that familiar with Ubuntus GUI or layout, though similar to Debian which has been my primary system for years.  So I can find my way around but not completely sure I'm putting everything in the right place or what I may be missing.

I finally found a work around to make the Tablet boot Linux even after I discovered the ia32efi file needed.  I installed Grub2 for Windows, with an unconfigured Menu option.  I can select it and it dumps back into the Bios, I can then select USB or the installed Ubuntu loader and they will will now generally boot fine.  Boot for some reason neither will boot without doing this work around.

I think I can probably configure Grub2forWin to chain-load the Ubuntu Grub giving me access to the updated Grub menu and Kernels there and a generic USB option maybe?  But that's not a big issue.

After I read a stray comment on a post that someone had sound working out of the box with Zesty, I installed that which fixed the audio and Bluetooth!

Now mostly trying to get the battery monitor working, I'm not completely sure but thought this line added to grub may help with that and possibly system hangs?  "intel_idle.max_cstate=0"  I've seen it with a "1" as well.

I also read that its possible to get a basic working touch screen.  I found info on a page for msl1680. [https://github.com/onitake/gsl-firmware/blob/master/firmware/rca/w101v2/README.md](https://github.com/onitake/gsl-firmware/blob/master/firmware/rca/w101v2/README.md)

I have the driver loaded and input on the screen.  Its just not functioning correctly enough to be usable.  

I used the xinput-calibrater, I can hit the crosses in the four corners.  I don't see how I can hit them and not the Icons etc.  Could there be a configuration in Ubuntu GUI itself?

I took the Calibration output and made a file where it said and added the output to the file.  It could be in the wrong place?  I put it here "/usr/share/X11/xorg.conf.d/99-calibration.conf"  it said there or "/etc/X11/xorg.conf.d/99-calibration.conf"  This directly didn't exist so I put it in the first one.

I have tried changing the "0" to "1" if that is the correct option to enable x/y invert but nothing changes but I know if I drag my finger right the window goes left, distance of where I place my finger to where it shows on the screen is also off.

Once I get those three things accomplished I have noticed scripts and tweaks for dock/undock rotation and brightness.  But not very important if the touch screen isn't working.

Thanks for any help, If you need more specific Info let me know and where it may be.  I don't remember commands, just how to look the up :)

---

### Post by howefield on 2017-01-16
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

