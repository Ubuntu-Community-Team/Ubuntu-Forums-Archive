---
title: "boot grub efi btrfs"
date: 2015-04-09
forum: Ubuntu Development Version
---

### Post by orj-gmail on 2015-04-09
[INDENT] 					I installed a beta (daily)ubuntu gnome. Installation worked and I   had ubuntu-gnome running. After 2 or 3 reboots when grub was showing up, choosing ubuntu only leads me to a grey screen. I made various fres installs, even with fresh burned isos.Always the same (could boot into windows via grub, this always worked). The ubuntu recovery didn't show various options, as I remember from 14.04 for example. I had the root and home partition always frmatted as btrfs. In my last install I formated root with ext4 and now the problem seems to be solved and the ubuntu-recovery in grub is showing some options. I googled around with boot;grub,efi,btrfs but I found nothing helpful. Is there any known problem with efi,grub and btrfs?

The isos were properly burned. Checked it.

64bit efi intel i7 8GB RAM 				dual boot ubuntu gnome/windows8.1
[/INDENT]

---

### Post by ventrical on 2015-04-09
> **orj-gmail said:**
> [INDENT]                     I installed a beta (daily)ubuntu gnome. Installation worked and I   had ubuntu-gnome running. After 2 or 3 reboots when grub was showing up, choosing ubuntu only leads me to a grey screen. I made various fres installs, even with fresh burned isos.Always the same (could boot into windows via grub, this always worked). The ubuntu recovery didn't show various options, as I remember from 14.04 for example. I had the root and home partition always frmatted as btrfs. In my last install I formated root with ext4 and now the problem seems to be solved and the ubuntu-recovery in grub is showing some options. I googled around with boot;grub,efi,btrfs but I found nothing helpful. Is there any known problem with efi,grub and btrfs?

The isos were properly burned. Checked it.

64bit efi intel i7 8GB RAM                 dual boot ubuntu gnome/windows8.1
[/INDENT]


I was just happenchance to be reading up on btrfs (which I have experimented with extensively)  and there were always some sorts of problems that I had encountered.  You want to know what and why. Honestly.. I forget atm but I can say that the btrfs system is only good  as a novelty because it takes such a long time to load and so much can go wrong ... not something I would use in development or stable unless it was cleaned up somewhat.

Regards...

---

### Post by orj-gmail on 2015-04-09
> **ventrical said:**
> I was just happenchance to be reading up on btrfs (which I have experimented with extensively)  and there were always some sorts of problems that I had encountered.  You want to know what and why. Honestly.. I forget atm but I cna say that the btrfs system is only good  as a novelty because it takes such a long time to load and so much can go wrong ... noit something I would use in development or stable unless it was cleand up somewhat.

Regards...

I can't be sure that the problems were caused by btrfs but it seems so. Btrfs for me (till now) seems to be ok for data partitions /home /storage but for /root  it causes problems. This as result of my "experiments". Thank you for your answer.

---

### Post by ventrical on 2015-04-09
There were big problems with Grub and btrfs as I recall. Grub would not recognize certain items.. etc..

---

### Post by ventrical on 2015-04-09
Here is one of many examples.

[http://ubuntuforums.org/showthread.php?t=2152656&highlight=btrfs+ventrical](http://ubuntuforums.org/showthread.php?t=2152656&highlight=btrfs+ventrical)

---

### Post by grahammechanical on 2015-04-09
If we installed on to a btrfs partition then that install of Ubuntu would show up at the top of the Grub boot menu but other installs of Ubuntu on btrfs partitions were not recognised by Grub's os-prober and so not in the menu.

If we have another install of Ubuntu on the machine and this second install has control of the boot menu, then its boot menu will not show the Ubuntu installed on a btrfs partition.

If we install apt-snapshot then we will get a recovery mode option of apt-snapshot - Revert to old snapshot and reboot. Which is useful. From 14.04 onwards Recovery Mode was put into an Advanced Options for Ubuntu submenu.

Whether any of this is related to your situation I do not know. That grey screen is the neutral background that the login screen and desktop are painted on to. This may be an issue with video drivers.

Regards.

---

### Post by orj-gmail on 2015-04-09
Whatever happened, but it seems ok now using ext4. Thanks a lot for your hints.

---

