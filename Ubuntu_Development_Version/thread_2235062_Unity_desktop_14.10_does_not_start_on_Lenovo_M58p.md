---
title: "Unity desktop 14.10 does not start on Lenovo M58p"
date: 2014-07-18
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2014-07-18
14.10 boots to wallpaper and cursor.  No panels, no launcher.  Pretty much disabled.
14.04 runs fine.
14.10 boot with nomodeset comes up O.K. in coarse 1024x768 screen mode and missing all the fancy unity effects.
Tried booting without nomodeset, to wallpaper only, Ctrl-Alt-F1 to issue ubuntu-bug linux.
Without unity couldn't get a browser up to report the bug.
Tried option K to keep the bug report at /tmp/apport.linux-image.....  however on rebooting there's no such bug report in /tmp or anywhere else.

This Lenovo desktop bios dated 1/2011

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

How do I issue a bug report?

Thanks

Update: multiple boots nomodeset and default finally got up and did an update & dist-upgrade.  Now running.

Let me go back to see if the .iso will boot to "Try Ubuntu...".  It didn't before.

"Try Ubuntu ..." still fails even on 20140718.  Background and two flashing icons (Install & one other).  No desktop can't do anything.  
Also, cannot do  ubuntu-bug on the "Try ubuntu..." version, packages missing....

---

### Post by cariboo on 2014-07-18
Have a look at the bug reporting [wiki]("https://help.ubuntu.com/community/ReportingBugs"), scroll down to Filing bugs when off-line.

---

### Post by jerrylamos on 2014-07-19
Thanks, I'll take a look at the wiki.

Meanwhile: 

tahr .iso boots fine.

20140719 .iso boots to a background with two flashing icons.  No desktop. Useless.

My bug report listed below, I don't know what a "bot" is:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1344504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1344504)

> Brad Figg (brad-figg) wrote 13 hours ago: Status changed to Confirmed	#2

This change was made by a bot.

---

