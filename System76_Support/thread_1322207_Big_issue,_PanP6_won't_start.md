---
title: "Big issue, PanP6 won't start"
date: 2009-11-10
forum: System76 Support
---

### Post by samh785 on 2009-11-10
I've been running my PanP6 for a few weeks now with only a few very minor issues. (I'm running karmic by the way). Today I installed the new updates, and installed flightgear. When I tried to run flightgear, it wouldn't start up and I thought this was odd so I decided to log out and back in again and see if it would work properly then. I tried to log out, but instead of it going to the login screen, it showed me some flickering words in the terminal and stayed there. I turned off the computer and then turned it back on. When I turned it on again the system76 bios displayed normally, and then the white ubuntu logo on the black background showed up.... all normal.... and then the flickering terminal showed up and prompted me for my username and pass. It is extremely difficult to enter any info this way, because the flickering seems to keep it from registering key presses 1/2 of the time. I rebooted the computer again, went into recovery mode and selected the option to repair broken packages. When this was done, I selected the option to update the grub bootloader. When this was done, I selected the option to clean up to free space. After this, I rebooted and tried to start it. No change. I'm in a panic mode right now, so any help would be GREATLY appreciated.

---

### Post by samh785 on 2009-11-10
so I booted into recovery mode, and ran
```
startx
```to start the xserver, and I get this:
```
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal Server error: 
no screens found
```Edit:
So I rebooted the computer once more. When the white ubuntu logo shows up, I pressed escape, and I guess this allows you to see the technical things that the computer is doing. Here is the code that it displays:
```
fsck from util-linux-ng 2.1628359-15b1-4eb6-a7c9-db1b40e7c807
/dev/sda1: clean, 171839/1831424 files, 1206118/3662109 blocks
fsck from util-linux-ng 2.16
/dev/sda6: clean, 7297/58753024 files, 5949908/117491909 blocks (check in 5 mounts)
*Starting init crypto disks...     [OK]
```and then the terminal starts flickering rapidly and continuously. It then provides this:
```
Ubuntu 9.10 system76-pc tty1

system76-pc login:
```all the while violently flickering. 
*sigh*

---

### Post by HotShotDJ on 2009-11-10
You went and installed the 190.* nvidia drivers, didn't you.  It probably got removed when you did the upgrade (with the 185.* installed, but not activated).

To fix:  You need to boot into recovery mode.  Reboot.  As soon as you see the word "Grub" in the top left corner of your monitor, press and hold the "shift" key until the Grub menu appears.  Choose to boot into recovery mode.

Once you get to a command line, type:```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```
Now, reboot.  Once you get up and running, you need to go to System -> Administration -> Hardware Drivers to get things back to good with NVidia.  Once you've done that, you can go back to the stuff we were talking about in your thread about compiz effects and adaptive scaling.  For now, don't use the 190.* drivers.

---

### Post by samh785 on 2009-11-10
> **HotShotDJ said:**
> You went and installed the 190.* nvidia drivers, didn't you.  It probably got removed when you did the upgrade (with the 185.* installed, but not activated).

To fix:  You need to boot into recovery mode.  Reboot.  As soon as you see the word "Grub" in the top left corner of your monitor, press and hold the "shift" key until the Grub menu appears.  Choose to boot into recovery mode.

Once you get to a command line, type:```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```Now, reboot.  Once you get up and running, you need to go to System -> Administration -> Hardware Drivers to get things back to good with NVidia.  Once you've done that, you can go back to the stuff we were talking about in your thread about compiz effects and adaptive scaling.  For now, don't use the 190.* drivers.
I uninstalled the 190 drivers and reinstalled the 185 drivers from the terminal, and it worked. Thank you though and if it ever happens again I'll use your command.

---

### Post by HotShotDJ on 2009-11-11
> **samh785 said:**
> I uninstalled the 190 drivers and reinstalled the 185 drivers from the terminal, and it worked. Thank you though and if it ever happens again I'll use your command.Excellent! I had suggested the recovery mode because I had thought you didn't have access to a regular boot.  Of course, if you can boot up normally, a simple installation of the drivers works just fine. :)

---

### Post by samh785 on 2009-11-12
> **HotShotDJ said:**
> Excellent! I had suggested the recovery mode because I had thought you didn't have access to a regular boot.  Of course, if you can boot up normally, a simple installation of the drivers works just fine. :)
I installed the drivers while in recovery mode, and then the normal mode became available :D

---

