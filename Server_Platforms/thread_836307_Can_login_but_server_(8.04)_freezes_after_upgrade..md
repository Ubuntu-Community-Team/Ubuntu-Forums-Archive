---
title: "Can login but server (8.04) freezes after upgrade."
date: 2008-06-21
forum: Server Platforms
---

### Post by TheWhopper on 2008-06-21
Hi Everyone!

Tried updating my Ubuntu Server for the first time and ran into a problem :(

PROBLEM: I can put in my user name and password, but it immediately freezes. The only thing on the screen is the bluish-greenish background, no icons or anything else.

CAUSE: I was trying to upgrade the server from 7.10 to 8.04 using these instructions [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) from a remote machine (Windows XP). It was upgrading for a while before it got to the openssh portion. It appeared to freeze and against my better judgment I rebooted the server. 

At this point....

1. Went into Rescue Mode

2. Selected /dev/sda1 as my device to use as a root file system

3. Selected 'Execute a shell in the installer environment'

4. #fdisk -l
Disk /dev/sda: 120.GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 *512 = 8225280 bytes
Disk identifier: 0x00936a4c

Device Boot      Start     End      Blocks       ID     System
/dev/sda1  *     1         14405    157708131    83     Linux
/dev/sda2        14406     14593    1510110      5      Extended
/dev/sda3        14406     14593    1510078+     82     Linux swap/Solaris

---

### Post by windependence on 2008-06-21
Can you get in from the command line? Try ctl+alt+backspace and kill the X server instead of logging in and see if you can log in at the command prompt.

-Tim

---

