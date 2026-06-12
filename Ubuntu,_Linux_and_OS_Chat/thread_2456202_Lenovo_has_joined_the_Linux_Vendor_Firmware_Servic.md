---
title: "Lenovo has joined the Linux Vendor Firmware Service"
date: 2021-01-06
forum: Ubuntu, Linux and OS Chat
---

### Post by #&amp;thj^% on 2021-01-06
Some of us may not be aware.
Red Hat’s Richard Hughes has revealed that tech company Lenovo, who produce the ThinkPad line of laptops, has joined the Linux Vendor Firmware Service, better known as the LVFS.

Tens of thousands of ThinkPad users will see firmware updates listed in GNOME Software in the coming weeks…

It’s a pretty big deal, with tens of thousands of Linux users set to benefit from the partnership.

But first, let’s recap what the LVFS is and why it’s becoming increasingly important to Linux users.

What is the LVFS?
Upgrading the firmware of motherboards, peripherals, and other hardware on Linux hasn’t been the easiest thing to do historically. Most major hardware vendors only provide ‘official support’ Microsoft Windows OS and only provide Windows-specific flashing tools to their customers.

Which is where the Linux Vendor Firmware Service comes in.

The LVFS helps OEMs, ODMs and other equipment makers to distribute UEFI firmware updates to Linux users. These firmware updates can be installed from inside the OS using a command-line tool or a GUI, such as GNOME Software.

The LVFS takes the hassle out of distributing firmware upgrades to Linux users, while fwupd takes the hassle out of installing them.
[list]
[*]OEMs don’t need to create manufacturer-specific tools
[*]Automatic detection of compatible hardware
[*]Users can install firmware updates alongside software updates via a GUI[/list]
Updating firmware on any OS, using any tool, can be scary: Multiple reboots! Terminal text spewing across the screen! Strange noises! So fwupd aim to make the process of updating firmware on Linux as automatic, safe and (most importantly) reliable as possible.

More info here: [https://linux.slashdot.org/story/18/08/06/1756240/lenovo-to-make-its-biosuefi-updates-easier-for-linux-users-via-lvfs](https://linux.slashdot.org/story/18/08/06/1756240/lenovo-to-make-its-biosuefi-updates-easier-for-linux-users-via-lvfs)
And Here: [https://forums.lenovo.com/t5/Other-Linux-Discussions/Linux-and-Firmware-Upgrade-in-general/m-p/4561607](https://forums.lenovo.com/t5/Other-Linux-Discussions/Linux-and-Firmware-Upgrade-in-general/m-p/4561607)
I remember having to keep a disk with MS installed to update my firmware and Bios. Snot any more) :)
IMPORANT NOTE: when running the upgrader you should not be in Legacy Mode, or you will see:
```
WARNING: Firmware can not be updated in legacy BIOS mode
  See https://github.com/fwupd/fwupd/wiki/PluginFlag:legacy-bios for more information.
Devices with no available firmware updates: 
 • PNY CS2311 1TB SSD
 • SAMSUNG SSD PM871 2.5 7mm 256GB
 • USB2.0 Hub
 • Unifying Receiver
Devices with the latest available firmware version:
 • Unifying Receiver
No updates available for remaining devices

```

This warning can be ignored if UEFI firmware updates are not desired. It can be disabled by adding
```

DisabledPlugins=test;invalid;uefi
```

to "/etc/fwupd/daemon.conf" or by recompiling without UEFI support.

**_Big HEADS_UP **WARNING**_**: If you change your BIOS mode from UEFI CSM/legacy to UEFI then you may have to reinstall all installed operating systems. A UEFI system requires an ESP partition and Linux installers do not typically create an ESP when run in legacy mode.
Go Lenovo/Linux

---

### Post by QIII on 2021-01-06
I don't know if this is a "lofty victory" for Linux so much as an acknowledgment that Linux desktop users, as few as we may be, represent a significant portion of highly technical users.

---

### Post by #&amp;thj^% on 2021-01-06
For a non MS user, it feels mildly lofty.

---

