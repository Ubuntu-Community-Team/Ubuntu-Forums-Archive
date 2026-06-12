---
title: "How to install Windows 10 on a Ubuntu PC ?"
date: 2015-10-17
forum: Windows
---

### Post by soamz on 2015-10-17
I was using my wife's PC as mine had gone for repair. 
I had installed ubuntu and now she needs windows 10 back on it, as she is totally blank with ubuntu and the command line. 

So, I have just got a bootable windows 10 64 bit USB drive. 

Now how do I format this ubuntu completely and install windows 10 fresh ?

Pressing F8 or F10 or F12, doesnt open the bootable option. 
How do I tell the PC to boot to USB ?

---

### Post by oldfred on 2015-10-17
Moved to Windows sub-forum

Dual boot or just erasing Ubuntu?

Newer UEFI or older BIOS system?

But either way you have to boot from flash drive or DVD installer. If USB drive is not seen as bootable it will not show as an option in UEFI/BIOS boot menu.

Windows only installs to gpt partitioned drives with UEFI, or only to MBR(msdos) partitioned drives with BIOS. So drive partitioning must match how you boot install media.

If new UEFI with secure boot, you may have to turn off Secure boot or enable/allow booting from USB drive. 

Even some older BIOS need USB settings in BIOS to work. Also some USB ports on some systems may work where others do not, or some flash drives may work where others do not.

 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

While I may use command line and post repair instructions with command line as then the flavor or gui you use does not matter, my wife does not even know what command line is.
She uses Thunderbird, Firefox for Facebook and general Web browsing, and Picasa for photos. Occasionally OpenOffice

---

### Post by soamz on 2015-10-17
Erase Ubuntu and install windows 10 completely.

---

### Post by yancek on 2015-10-17
When you boot the computer, you should see the manufacturer logo and at the bottom of that windows a message indicating which key to use to enter BIOS setup.  You need to then find the option to change the boot priority and it may be listed under hard drives or usb drives.

---

### Post by soamz on 2015-10-17
> **yancek said:**
> When you boot the computer, you should see the manufacturer logo and at the bottom of that windows a message indicating which key to use to enter BIOS setup.  You need to then find the option to change the boot priority and it may be listed under hard drives or usb drives.

Its connected to a wireless keyboard and its doesnt work until ubuntu screen comes up. 
I think to reach BIOS, have to connect a wired keyboard.

---

### Post by oldfred on 2015-10-17
Some UEFI have a fast boot setting. That assumes you have no hardware changes and just starts system, before you even have time to press a key. While configuring systems you need to have that fast boot off.
Most will let you normal boot from a cold or power off boot. You may have to totally shutdown, remove battery if laptop, and hold power switch to drain any left over power. 
A few have had to jumper pins on motherboard, or have a reset switch under laptop, or remove motherboard battery. One early brand UEFI system had to be returned to vendor.

---

