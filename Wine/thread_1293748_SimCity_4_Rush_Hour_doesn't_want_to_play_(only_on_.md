---
title: "SimCity 4 Rush Hour doesn't want to play (only on my system)"
date: 2009-10-17
forum: Wine
---

### Post by tghe-retford on 2009-10-17
No matter what I do or what settings are set in Winecfg, SimCity 4 Rush Hour simply refuses to play nice. All that appears in the terminal when I run it is this:
```
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eed4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f58c,0x00000000), stub!
```
And then I am dropped back to the prompt, and the wineserver is killed.

Noticing in the Wine AppDB that someone got it working with 1.1.30, I installed that version and the same thing happens, so it is not a regression. I deleted the old Wine directory and started afresh prior to this.

Other Wine applications I have such as Spotify run fine.

Anyone know what would cause SimCity 4 Rush Hour to simply stop working?

---

### Post by hikaricore on 2009-10-17
There are no errors in that output so it's 100% unhelpful.
You're going to have to give some more info such as hardware.

---

### Post by tghe-retford on 2009-10-17
As requested:

CPU: Intel Core 2 Quad Q6600 G0 Stepping (2.4GHz 1066MHz) Socket 775 L2 8MB Cache (2x4MB (4MB per core pair))
Memory: 2GB DDR2 800Mz/PC2-6400 Memory REAPER X EDITION ENHANCED BANDWITH CL4
Graphics card: Zotac 8800GT AMP Edition 512mb GDDR3 Dual DVI PCI-E Graphics Card using NVidia 190.36 drivers from PPA. Dual monitor setup: Samsung SyncMaster T220 at 1680x1050 - 60Hz and LG L1919S at 1280x1024 - 60Hz.
```
Output of: glxinfo | grep rendering
direct rendering: Yes
```
Sound: Realtek ALC883 6-channel (using HDA Nvidia) on-board motherboard sound, using coaxial output to surround sound system.
Motherboard: Asus P5N-E SLI 650i Socket 775 PCI-E Onboard Audio ATX Motherboard
Wine: 1.1.31~winehq0~ubuntu~9.04-0ubuntu1

I knew there would be a time when I kept this information somewhere that I would need it.

Have also tried this, knowing that SimCity 4 can be problematic with resolutions, particuarly for widescreen monitors:

```
wine '/home/sonic/.wine/drive_c/Program Files/Maxis/SimCity 4/Apps/SimCity 4.exe' -r1680x1050x32 -CustomResolution:enabled -d:opengl
```

and still the same problem.

---

### Post by hikaricore on 2009-10-17
You mentioned the appdb page, did you read the instructions listed there?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500&iTestingId=26634](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500&iTestingId=26634)

I personally don't have this title so I won't be able to help much but sometimes all you need is someone to point in the right direction.  :p
The posts on this one a pretty confusing and each user seems to be contracting the one before them.  >.< That can't be helpful.

---

### Post by tghe-retford on 2009-10-17
I know about all the information on the appdb pages for SimCity 4 (Rush Hour/Deluxe) and nothing will work. I created a bug report:

[http://bugs.winehq.org/show_bug.cgi?id=20404](http://bugs.winehq.org/show_bug.cgi?id=20404)

---

### Post by HappyLinux on 2011-03-11
> **tghe-retford said:**
> I know about all the information on the appdb pages for SimCity 4 (Rush Hour/Deluxe) and nothing will work. I created a bug report:

[http://bugs.winehq.org/show_bug.cgi?id=20404](http://bugs.winehq.org/show_bug.cgi?id=20404)

Sounds like you're having a problem with one of your games my friend. Did you manage to get any of those games that I gave you a couple years ago to work?

I'm thinking about trying out Homeworld: Cataclysm on my Ubuntu.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14776](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14776)

There's no chance it'll work in my Win7.

---

