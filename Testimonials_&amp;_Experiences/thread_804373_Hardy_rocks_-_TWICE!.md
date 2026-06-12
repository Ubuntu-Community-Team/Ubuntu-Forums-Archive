---
title: "Hardy rocks - TWICE!"
date: 2008-05-23
forum: Testimonials &amp; Experiences
---

### Post by Thanh-BKK on 2008-05-23
Hellooooo :)

Well, prior to putting Ubuntu on my main machine i was playing around with it on a second, spare, computer. I had a bunch of problems there as the onboard graphics card didn't want to support 3D (it's a SiS) and the old AGP that i had (Nvidia TNT 2 M64) needed a driver from Nvidia directly which refused to work.... lotsa hickhack.

However AFTER Ubuntu started powering my main machine, i went back to that little one and tried to pimp it up. So i got a new Nvidia AGP (GeForce 6200) but with that, Ubuntu wouldn't even boot. Not even the live CD! Regardless what option i chose. I then decided that the mainboard must be the problem.

Yesterday i obtained another mainboard, fairly new, with attached Athlon XP 64 3500+ and 1 GB of DDR-II RAM. In fact my boss told me i can take that if i want it as nobody uses that machine (it's one i built end of last year for the office). So i took it home and really, it fits into the small computer (one of these compact ones). It has onboard graphics too, but also a PCI-E slot! And i still had my old ATI x300 sitting there. Quickly slotted that in and did a test boot with the Ubuntu live CD - WORKED!!

So in the morning today i installed the system, and had a perfectly working Hardy in less than half an hour on that machine (took long at 82% "scanning the mirror", same as on the main machine). 

I then installed the restricted ATI driver from the repo - and it still worked just fine!

BUT then came the dreaded updates. 89 of them. And after they were done, reboot - and zap bang - low resolution. Could not correctly identify graphics card and/or monitor. Oh how nice.

After a bit of tinkering i had it back working, minus that restricted driver, and unable to enable desktop effects. So i just enabled that driver again - and rebooted.

After login, i got an all-white screen. 

CTRL-ALT-Backspace, re-login - same. CTRL-ALT-Backspace, chose session, Gnome failsafe - i was back in. disabled that driver, and all was well again. Now i could even enable desktop effects! I then installed the Compiz manager and chose a few items i like (cube etc), rebooted again - all worked. BUT - machine was sluggish, something took up 100% CPU. Compiz? No idea, System monitor didn't want to tell me. 

So i enabled that wicked driver again, reboot - and the bloody white screen again!!

Aaaaargh.

Gnome failsafe, DISabled that driver again, reboot - and everything worked fine! All effects "on" as desired, machine fast and snappy. CPU idles at 4% (which is System Monitor itself). 

I did a whole bunch of reboots, even installed AWN inbetween just to test - it stayed that way. 

And, man, that little machine seriously kicks ***! I probably don't have TV-out working bot on that one i won't need it anyway, that's my test machine. I'll install Kubuntu and Xubuntu desktop on it to test drive those, and a bunch of software. It's only a 30 GB HDD in there.

So, after some hiccups in the beginning, i can say now - for me, Hardy rocks TWICE already :)

And a curious question - since the "restricted driver" is disabled and i didn't download any from ATI, what is it running on now? As all effects work........

Best regards.....

Thanh

---

### Post by ukripper on 2008-05-23
Glad to know it works for you too!!!:guitar:

---

### Post by wolfen69 on 2008-05-23
> **Thanh-BKK said:**
> since the "restricted driver" is disabled and i didn't download any from ATI, what is it running on now? As all effects work........
 
welcome! you mean you have the cube working without the driver?

---

### Post by Thanh-BKK on 2008-05-23
Hi :)

Yes, exactly that. The restricted driver is NOT "enabled" and says "NOT in use" but i got the wobbling windows, window previews and the cube, perfectly working. 

I have just spent three hours downloading and installing stuff on that box, but now i have already shut it down, but i did look at the xorg.conf and it mentions neither "fglrx" nor "mesa" but instead "ATI" as driver.

Can that be? If so, which one is that?

But i am certainly not complaining about the fact that it works so well.... could have been a lot worse with that ATI, i was already mentally prepared to buy another Nvidia :) Glad i can put my ATI to a good use.

Best regards.....

Thanh

---

### Post by JC Cheloven on 2008-05-23
Nice to hear about your (almost) positive experience. You were quite very patient. Some other people give up with far more minimal issues (and post a "bye bye" thread yust to let people know how fickle they are :-) )

It's strange how different the experiences of the users can be. I had my bigger successes with hardy when installing on older hardware [http://ubuntuforums.org/showthread.php?t=786667](http://ubuntuforums.org/showthread.php?t=786667) , while it's the opposite for you. 
Regards

---

### Post by JC Cheloven on 2008-05-23
N

---

### Post by wolfen69 on 2008-05-23
> **Thanh-BKK said:**
> Hi :)

Yes, exactly that. The restricted driver is NOT "enabled" and says "NOT in use" but i got the wobbling windows, window previews and the cube, perfectly working. 

I have just spent three hours downloading and installing stuff on that box, but now i have already shut it down, but i did look at the xorg.conf and it mentions neither "fglrx" nor "mesa" but instead "ATI" as driver.

Can that be? If so, which one is that?

But i am certainly not complaining about the fact that it works so well.... could have been a lot worse with that ATI, i was already mentally prepared to buy another Nvidia :) Glad i can put my ATI to a good use.

Best regards.....

Thanh

well, you obviously have the driver and it is working. but for some reason it is showing up as not enabled. either way it is working, so it's good to hear.

---

### Post by Thanh-BKK on 2008-05-24
Hello :)

I'm posting from that very computer right now. I have just checked - nope, the "ATI accelerated graphics driver" is there but NOT "enabled" and "not in use", yet the wobbling windows, window preview, cube etc all work just fine. I am NOT complaining about that! Here's my xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1280x960@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

I don't know enough about these to start trying out things blindly, if someone here could just tell me why my 3D stuff can work despite the driver not being there? But i certainly won't change anything :)

Right now i am downloading both Kubuntu and Xubuntu packages so i can switch desktops and compare...... i hope it won't break stuff :)

And finally, here's a screenshot of this beauty :)

With kind regards.....

Thanh

---

