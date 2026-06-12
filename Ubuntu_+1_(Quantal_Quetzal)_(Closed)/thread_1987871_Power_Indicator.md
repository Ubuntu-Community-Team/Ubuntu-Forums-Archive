---
title: "Power Indicator"
date: 2012-05-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-05-26
running 12.10 on compaq presario laptop and have no power indicator for battery or ac power

---

### Post by pal1965 on 2012-05-26
..me too on asus laptop ....

---

### Post by cariboo on 2012-05-26
Neither of you stated if you are running an upgraded 12.04 install, or a fresh install from a daily iso. This information would help immensely.

---

### Post by pal1965 on 2012-05-27
..it's a fresh install for me....I have an asus k53SD...

---

### Post by jerrylamos on 2012-05-27
> **cariboo907 said:**
> Neither of you stated if you are running an upgraded 12.04 install, or a fresh install from a daily iso. This information would help immensely.

I'd love to ... couldn't boot off the .iso Squashfs gets myriad errors and can't find lots of things.  Works on Precise, Oneiric, Maverick, Lynx, ...

Tried to boot from a loop mount installed on a 1G partition.  Squashfs can't find lots of things.  Works on Precise, Oneiric, Maverick, Lynx, ...

Tried booting the iso hybrid.  It wouldn't.  I'll try that again.  dd is pig slow.  Gparted got an error and crashed but I think the format F32 went O.K.

Tried making startup disk using Quantal.  Partway thru the startup disk window disappeared, tiny window about copying & installing boot seemed to go to completion .  The USB starts to boot, screen goes blank.  Could try making the startup disk with Ocelot.

I've got both quantal updated from precise and from an install a while back, this one shows no battery indicator on Acer 5253 notebook.  I haven't looked at systems settings.  Oof, Alt-Tab doesn't work again!! and workspace switcher is being very flunky.

It isn't even Alpha 1 yet, but I'll see if I can get some kind of install going.

Jerry

p.s.  Can't say I didn't ask for this....

---

### Post by fjgaude on 2012-05-27
I'm running an upgraded install from 12.04 to 12.10 on my Dell mini 10". Have no issues with it, except it will not suspend.

In 12.04 it is perfect with all functions.

I did a clean install of 12.10 on my main box using an USB HHD...just looking and reporting bugs... none to speak of yet.

---

### Post by jerrylamos on 2012-05-27
Updated to #8 power indicator came back O.K.  It even seems to work.

Let's see if it is working on a fresh install:

Today's May 27 zsync of .iso ran clean, checksums matched.

Startup disk creator to USB worked O.K.

Booted on this Acer Aspire 5253 AMD E-360 X 2 splash screen shows up, the little dots march across.  After 5 minutes I gave up and Ctrl-Alt-F1

SQUASHFS ERROR: glibc_inflate error, data probably corrupt
squashfs_read_data failed to read block OX6994941
unable to read fragment cache entry

Well, try again another day.

Jerry

---

### Post by cariboo on 2012-05-27
To get this back on topic, do you have indicator-power installed?

---

### Post by fjgaude on 2012-05-28
I do and it works on both of my machines.

---

### Post by pal1965 on 2012-05-28
...I checked and it's installed...

---

### Post by jerrylamos on 2012-05-28
> **cariboo907 said:**
> To get this back on topic, do you have indicator-power installed?

Hope this isn't a silly question, how do I "install indicator-power" on my Acer Aspire One netbook?  This is 
Linux USBHD 3.4.0-3-generic #8-Ubuntu SMP Sat May 26 01:44:29 UTC 2012 i686 i686 i686 GNU/Linux.  
Right click on panel doesn't do anything, I couldn't see anything on install power indicator in "System Settings", or in search for applications.

On my Acer 5253 notebook the power indicator did show up after upgrading to ....#8.

Jerry

---

### Post by cariboo on 2012-05-28
> **jerrylamos said:**
> Hope this isn't a silly question, how do I "install indicator-power" on my Acer Aspire One netbook?  This is 
Linux USBHD 3.4.0-3-generic #8-Ubuntu SMP Sat May 26 01:44:29 UTC 2012 i686 i686 i686 GNU/Linux.  
Right click on panel doesn't do anything, I couldn't see anything on install power indicator in "System Settings", or in search for applications.

On my Acer 5253 notebook the power indicator did show up after upgrading to ....#8.

Jerry

Open up synaptic or the software centre, and search for indicator-power, this is for Ubuntu, I don't know if it would be the same for Lubuntu.

---

### Post by jerrylamos on 2012-05-28
> **jerrylamos said:**
> Hope this isn't a silly question, how do I "install indicator-power" on my Acer Aspire One netbook?  JerrySolved.  Today's update got the power indicator back.

Jerry

---

### Post by pal1965 on 2012-05-28
..Solved for me too with the last update...

---

### Post by jerrylamos on 2012-05-28
> **pal1965 said:**
> ..Solved for me too with the last update...
Spoke too soon.  Just did an install of 28 May i386 quantal and the battery power indicator is nowhere in sight.  I did an update even.

Jerry

---

### Post by kuvanito on 2012-05-28
i did not subscribe to the thread i created
i do not do upgrades from prev vers,my installs are always fresh and clean
still no power ind and there for my machine shutsdown when the juice is gone and i have no way to tell....i know it will be fixed....

---

### Post by pal1965 on 2012-05-29
...vanished again......

---

### Post by jerrylamos on 2012-05-29
Fresh install 20120528 i386 image on Acer Aspire 5253 wide screen notebook

No battery indicator.  Actually did the install on battery.

Description:	Ubuntu quantal (development branch)
Release:	12.10
Codename:	quantal
Linux version 3.4.0-3-generic (buildd@vernadsky) (gcc version 4.7.0 (Ubuntu/Linaro 4.7.0-7ubuntu4) ) #8-Ubuntu SMP Sat May 26 01:44:29 UTC 2012

Booted a couple of times indicator still not present.  Ubiquity knew it was running on battery.

Jerry

---

### Post by mc4man on 2012-05-29
Check your syslog, should have some lines about Battery Slot & battery present

(can't imagine your indicator icon-policy is being set to never

---

### Post by effenberg0x0 on 2012-05-30
+1 on this problem for a while.

After wasting some time with it I just realized indicator-power is always running for me. But it only shows when there's an icon for it in the icon-set I am using. Which is kind of obvious :) 

Maybe some of the people that reported it are also trying some theme customization?

Regards,
Effenberg

---

### Post by jerrylamos on 2012-05-30
> **cariboo907 said:**
> Open up synaptic or the software centre, and search for indicator-power, this is for Ubuntu, I don't know if it would be the same for Lubuntu.
Synaptic says indicator-power is installed:```

indicator-power     2.0-0ubuntu1   indicator showing power state
```
There's no battery status indicator on the top panel, Unity-2D, installed 2 days ago and updated daily including today.  

Same thing on Acer Aspire 1 netbook and on Acer Aspire 5253 widescreen notebook.  I do need to keep track of the battery charge state on them.

?  

Thanks, Jerry

---

### Post by pal1965 on 2012-05-31
..fresh install yesterday with [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-amd64.iso) ..power indicator ok

---

### Post by jerrylamos on 2012-06-01
Install fresh today 1 June no battery indicator on Acer Aspire 1 netbook.  Seems to come and go from install to install.  Yes, "indicator-power" is shown as being installed, if that's the one that does battery status.

Jerry

---

