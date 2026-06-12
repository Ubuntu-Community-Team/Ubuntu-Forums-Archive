---
title: "xenial desktop did not start"
date: 2016-03-19
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2016-03-19
Xenial running here fine for months.  I do a periodic install to check for bugs etc.
Using ubuntu xenial daily build from today 19 March::
xenial-desktop-amd64.iso       07-Mar-2016 13:05  1.5G  Desktop image for 64-bit PC (AMD64) computers (standard download)
installed in another partition.  Install went fine.
Boots to command line.  No desktop.  Recovery does the same.

Tried both the updated 4.4.0-14 and the 4.4.0-10.  Same thing.

Some complaint I couldn't understand about "Upstart".

Any way to start Xenial desktop?

Any more current Xenial .iso?  daily build is quite a few days back and several linux images back.

Thanks.

DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu Xenial Xerus (development branch)"
Linux Lenovo2 4.4.0-14-generic #30-Ubuntu SMP Tue Mar 15 13:04:17 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

---

### Post by Doug S on 2016-03-19
Hi Jerry,

I did an install from the daily just three days ago, and it was O.K.

Today's daily seems to be a significantly different file size than three ago, so I don't think it is the same file. My md5sum agrees with what is [listed]("http://cdimage.ubuntu.com/daily-live/20160318/MD5SUMS") on the web site. Here is what I have from the last few days:

```

-rw-rwxr--  1 doug         doug 1578270720 Mar 11 12:38 xenial-desktop-amd64-20160311.iso       md5sum: baad947fee77c157a5f1cf1387cadb67
-rw-rwxr--  1 libvirt-qemu kvm  1579827200 Mar 16 10:59 xenial-desktop-amd64-20160316.iso     md5sum: 757221027480a85edcd3f6cb6a9325ea
-rw-rwxr--  1 doug         doug 1599602688 Mar 19 15:02 xenial-desktop-amd64-20160319.iso       md5sum: b34b9cf91743d901f3c4814b0a831376
```

It will be several hours, or not even today, before I have a chance to try to install todays ISO. I'll report back once I do.
I got the iso from [here]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/114888/downloads").
And I would typically fill in [the test case on the qa tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds") during / after an install.

---

### Post by jerrylamos on 2016-03-19
Thanks for the hint.  Daily Live Current is way behind.
Tried Daily Live Pending same problem.  Boots after install but not after apt-get update, apt-get dist-upgrade, Samba, so as motivation goes will check to see if anything installed post update is a difficulty.
Did an ubuntu-bug on the boot desktop failure.

---

### Post by jerrylamos on 2016-03-20
Found it.  Starting in November 2014 Ubuntu X windows screwed up with 
VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
making Wallpaper badly hashed.  
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)
Then a couple months later even Ubuntu text badly garbled, illegible.
Workarond was:

```
/usr/share/X11/xorg.conf.d/20-intel.conf
Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
Option "AccelMethod" "uxa"
EndSection
```

So in every install since Nov. 2014 I've been making that change.
As of March 2016, that change screws up X windows and can't get desktop.

Voila, not needed, Xwindows now running fine.  That took Ubuntu a year and a half to fix.
Wonder how long ubuntu Xwindows will stay fixted....

---

### Post by sudodus on 2016-03-20
Interesting that UXA acceleration is not longer needed and does not work with Xenial, at least not with your graphics chip :-)

---

### Post by Doug S on 2016-03-20
Hi Jerry,

I hadn't seen your posting, when I tried a new install on my VM this morning. I had some VM issues, but in the end it installed and re-booted O.K.
I did today's, 20th, ISO:

```
-rw-rwxr--  1 libvirt-qemu kvm  1599602688 Mar 20 08:13 xenial-desktop-amd64-20160320.iso  md5sum: 4ae4a24ebc39dcd990da2ae71b2edfad
```

---

### Post by ventrical on 2016-03-20
Same thing from 2 days ago. USB will boot up in UEFI mode but I get COM32 command line boot: in BIOS mode.

 reagrds..

---

### Post by crcarson on 2016-03-21
Had been having intermittent boot "to blank screen" but after yesterdays update can no longer boot 16.04 gnone.  Get a blank screen after the password and cannot do anything with the system except power off/on.  Do not have the 20-intel.conf on the system and adding it doesn't help.  Running controller

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
        DeviceName:  Onboard IGD
        Subsystem: ASUSTeK Computer Inc. Device 8534
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at df800000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915

Jerry, what is the bug number you opened?

---

### Post by crcarson on 2016-03-21
You can out wait the blank screen.  Was trying different things at the blank screen and the desktop appeared.  Had nothing to do with what I was trying just waiting 1 1/2 to 2 minutes and the desktop comes up.  "systemd-analyze blame" command shows no problems.

---

### Post by crcarson on 2016-03-21
Looking at the Xorg log from a failing boot shows these entries (comparing with what I think is a good boot which doesn't show these)

[    22.582] (II) systemd-logind: got pause for 13:64
[    22.582] (II) systemd-logind: got pause for 13:75
[    22.582] (II) systemd-logind: got pause for 13:66
[    22.582] (II) systemd-logind: got pause for 13:67
[    22.582] (II) systemd-logind: got pause for 13:76
[    22.582] (II) systemd-logind: got pause for 13:65

The delay if those are pauses in seconds is just less that the boot delay I see.

---

### Post by crcarson on 2016-03-26
This continues to be a problem although intermittent (every other or third boot) the system has a black screen for 90 seconds right after entering the password at login.

---

