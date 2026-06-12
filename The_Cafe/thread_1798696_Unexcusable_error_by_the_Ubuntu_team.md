---
title: "Unexcusable error by the Ubuntu team"
date: 2011-07-06
forum: The Cafe
---

### Post by dago1 on 2011-07-06
Yesterday I made a bootable USB drive using the latest Ubuntu release to install in my brand new laptop. I connected the USB, booted from it and got the error: 

"unknown keyword in the configuration file"

*ok lets do a quick google search to see what is the problem*

*oh, it seems I need to change a line in the /syslinux folder*

So I  browsed to the root directory of the USB disk, clicked on the 
/syslinux folder, and opened the file entitled syslinux.cfg.

Using a text editor, fund the line:
ui gfxboot bootlogo

 Changed it to:
gfxboot bootlogo

I booted from the USB and Installed the latest Ubuntu release without a hitch.


So, in the grand scheme of things Ubuntu just works right?

NO!

Lets get down from our technical high horse and analyse what happened.

1. Bootable drives made following the instructions in the Ubuntu homepage will be useless.

2. Persons trying Ubuntu for the first time will be left with a bad impression.

3. That particular error is in no way shape or form the fault of the end user.

Someone who is not that technically minded will not hunt for a solution, he or she will not use a text or code editor to look for "sislinux.cfg"
and change some obscure line in the configuration file.

Ubuntu, one of the most highly touted operating systems is failing to even boot for dozens of potential new users. I hope this issue is resolved.

---

### Post by dniMretsaM on 2011-07-06
This doesn't happen on 99.9 percent of Live CD's/USB's/DVD's. I've never had it happen. It's just a small glitch that happens on an occasional install. I'd like to see you run Windows and never have any problems booting...

---

### Post by snowpine on 2011-07-06
Have you reported the bug through the proper channels, so it will actually get fixed in the next release and save other users the same frustration? :)

---

### Post by marshmallow1304 on 2011-07-06
Looks like the problem is not from Ubuntu CD itself but from the Startup Disk Creator program.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/645818](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/645818)

> It is not possible to create Ubuntu 10.04 USB disks from the Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility in the syslinux program.
[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Common_Desktop_applications](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Common_Desktop_applications)

---

### Post by uRock on 2011-07-06
I haven't had this problem. I create bootable USBs often. I do have a bug report for the USB-creator-gtk requiring so many passwords to make the things. [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/789242](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/789242)

---

### Post by cariboo on 2011-07-06
Whatever utility you used to create the usb device is to old, syslinux was updated to a newer version back around Lucid. If you created it in Ubuntu, you need Lucid or newer, I'd suggest the latest version of unetbootin for Windows.

---

### Post by timZZ on 2011-07-06
People make mistakes! Trust me ...

---

### Post by jvgeli on 2011-07-08
Ubuntu is not the problem its the USB creator, you were probably using an old version. had the same issue when I used an old version of Unetbootin, the Syslinux folders and cfg's were just wrong and had to edit them manually. Now, i tried using the latest Unetbootin and it works. Also, it may be wise in the future to file the complaint/issue on the proper channels and don't blame people right away if verifications haven't been made yet. It just makes you look like a nagger. 
 
Good Luck!

---

