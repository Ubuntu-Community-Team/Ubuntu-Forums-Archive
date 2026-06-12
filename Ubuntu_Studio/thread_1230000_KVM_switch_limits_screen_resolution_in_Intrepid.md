---
title: "KVM switch limits screen resolution in Intrepid"
date: 2009-08-02
forum: Ubuntu Studio
---

### Post by truetech08 on 2009-08-02
I've just installed a Belkin Flip VGA USB w/audio KVM switch.  I run Intrepid on my laptop and desktop.  After booting my desktop cleanly through the KVM, (and many reboots), I only have a max res of 1024x768.  The monitor abilities don't seem to be detected anymore.  I run Nvidia drivers, and the Nvidia X Server settings in System - Admin allows me to assign a wacky 1152 x 864 resolution, but it doesn't look right.  I was running 1280 x 1024 @ 75hz just fine without the KVM.  Another weird thing is when I start Firefox, I can't minimize or switch to desktop, or copy/paste from that window to anything else, there's no title bar at the top.

I think that I need to force Ubuntu to allow a higher res than it thinks the monitor can handle.  I've tried editing my xorg.conf file by following some other posts, but mine doesn't look like anyone else's, and I'm not even sure if that's what I need to do.  Has anyone else solved this kind of problem?  Code from xorg.conf file below, typed manually on my laptop because can't copy from file into Firefox:

Section "Monitor"
             Identifier                   "Configured Monitor"
EndSection

Section "Screen"
            Identifier                  "Default Screen"
           Monitor                    "Configured Monitor"
            Device                   "Configured Video Device"
            DefaultDepth          24
EndSection

Section "Module"
             Load           "glx"
EndSection

Section "Device"
             Identifier               "Configured Video Device"
             Driver                   "nvidia"
            Option                   "NoLogo"                "True"
EndSection

---

### Post by marfal on 2009-08-07
Ditto!

I'm messing around with two old Dell boxes on an old fujitsu siemens TFT monitor. When monitor is plugged directly into either of the pc's it defaults to a 1024x768 60HZ resolution.
However through the KVM switch I can't get more than 800x600 (no higher option in system-preferences-display).

I've wasted best part of a day on this, trawling forums etc.
Help needed please.

xorg (from booting with monitor plugged into pc)

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by truetech08 on 2009-08-09
Wow, usually I get a response within a day or two.  Where have all the experts gone?

---

### Post by wkulecz on 2009-08-11
I'm running IOGear 2-ports and AirLink 4-ports at 1920x1200 with no issues over the VGA connector with a variety of Ubuntu(9.04, 8.04, 6.06) and Windows systems using Nvidia cards. 

These are KVM only, no audio, I've cheap speakers plugged in wherever I need audio -- if I need audio, I don't want it to switch and not be heard if I'm not looking at it.

Perhaps the issue is a limitation of the KVM you have?

Some systems have been setup through the KVM, others the KVM was added afterwards, and as I said they all "just work".

--wally.

---

### Post by marfal on 2009-08-11
Ok, I'm sure it's an issue with ubuntu not being able to detect the monitor properly.
When I'm connected directly to PC, although I can get a max resolution of 1024x768 the display is labeled "Unknown".
It's a Fujitsu Siemens model- 1560A+
Not sure why it's not picking it up but never worried about as I was getting an ok resolution.
Through the KVM switch I can't achieve better than 800x600.
I can boot with the monitor plugged into the pc to get 1024x768 then plug it into the KVM and maintain the 1024x768 resolution but booting plugged into the KVM switch, resolution drops to 800x600.

I need a way to fix my screen resolution at 1024x768, regardless of the screen plugged in.

Thanks

---

### Post by wkulecz on 2009-08-11
This question might get better answers in the Multimedia and Video Forum instead of here since its not really a media production issue.

> Ok, I'm sure it's an issue with ubuntu not being able to detect the monitor properly

Actually from your description it seems Ubuntu is picking up your monitor's capabilities correctly, but the KVM switch is not passing them on to Ubuntu, thus defaulting to 800x600.

I've long forgotten (good riddence!) about the verious sections of the xorg.conf file, but I think in the "SCREEN" section there used to be a line listing the allowed resolutions and another to set the default.  Unfortunately this may all be automagic now with all the possibilities listed and then ones removed that the monitor query during boot suggests won't work.  I assume a manual override still exists, but I can't offer any other help.  If you can't find out about the manual overide, you'll need a better KVM.

Does CtrlAlt+ and CtrlAlt- cycle through the supported resolutions?  It doesn't on my Ubuntu 8.04 system I have in front of me, so things may be so automated now that these old ways no longer work. 

--wally.

---

### Post by truetech08 on 2009-08-12
Thanks for your help wkulecz, I will repost on the correct forum, must have clicked the wrong link.  For my problem, you're absolutely right, the KVM isn't passing along the info from the monitor.  Ubuntu detects my monitor without issue when not using the KVM.  Hopefully someone in the other forum can help force the correct resolution.

---

