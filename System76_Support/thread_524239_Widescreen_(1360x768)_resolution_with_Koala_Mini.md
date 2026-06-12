---
title: "Widescreen (1360x768) resolution with Koala Mini"
date: 2007-08-12
forum: System76 Support
---

### Post by Paradoxdruid on 2007-08-12
Hello System76 support,

My little first-edition Koala mini has been serving great as my media hub for quite some time now.  Situations change, however:  I finally bought a new LCD TV (a Vizio vx37l 37 in LCD TV), and I'm having trouble setting the Koala to a widescreen resolution so that everything isn't squashed onscreen.

Right now, it's supporting 1280x1024 at 60 Hz just fine on the TV, but it won't output a signal at 1280x768 (a suggestion from the Ubuntu forums archive) or 1360x768 or 1366x768.

The system is using the i810 video driver, and is connected via VGA cable.

Any ideas of resolutions / video modelines / something else that could help me get a widescreen picture?

Thanks!

Edit:  here's the relevant xorg.conf sections:
> Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Vizio VX37L"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Vizio VX37L"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


---

### Post by thomasaaron on 2007-08-13
Did you try running: sudo dpkg-reconfigure xserver-xorg and trying to enable higher resolutions?

Note: You may have to lower your color depth to around 16 to achieve that resolution.

---

### Post by Paradoxdruid on 2007-08-13
I didn't want to post more details of my attempts until I saw if anyone had a set solution, but I guess not.

I've run dpkg-reconfigure xserver-xorg over a dozen times, trying different settings.  It never offers widescreen geometries (it's apparently an i810 driver issue).

So I followed some advice from the Ubuntu Wiki and installed xserver-xorg-video-intel , which replaces the i810 driver with a newer, intel one.  This still didn't offer widescreen modes on xserver reconfiguration, but it sent not usable signal to the monitor.  (The Xorg log file showed the intel driver was sending signals to either path A (VGA port) or path B (S-video port), and it had set the X signal to path none.  I have no idea how to force the intel driver to actually send a signal.)

Reinstalling the i810 driver, I could at least get the display working.  It actually works to send 1024x768 at 16 bits (or 1280x1024, which it must be rescaling in the TV) and get a crisp but stretched picture.  I found a TV mode which centers it instead of stretching it, so I can get good resolution--  but only 4:3 ratio.

I still want full 16:9 ratio for the screen, so I tried installing the 915resolution package and manually changing the Video BIOS to offer 1360x768--  it made the driver (from the Xorg log) not find a usable mode and shutdown.

So...  I'm out of options.   I **think** the solution lies in installing the xserver-xorg-video-intel package, but I can't get it to send signal correctly.  Maybe I need to add a modeline or a setting to force a certain output in my Xorg.conf


Any ideas?

---

### Post by thomasaaron on 2007-08-16
I did some more research on this one.

It actually looks like your problem is pretty common. However, every thread and bug report I can find on it leaves the situation unresolved. The consensus seems to be that Ubuntu just doesn't support it yet via the i810 chip.

---

### Post by Paradoxdruid on 2007-08-17
Thanks for the reply, thomasaaron.  That's kind of what I was suspecting.  

It doesn't hurt, in any case.  Even if it isn't widescreen, the Koala displays beautifully on the TV, and I "tricked" it into displaying movies correctly.  I edited mplayer's config to set the aspect ratio to always be 16:9, so it looks scrunched when the signal is normal, but then I set the TV to widescreen mode, and the image looks perfect, and my DVDs play in glorious widescreen.

---

### Post by tedrampart on 2007-08-17
is there a DVI output on the koala?  if so, you could try getting a DVI-HDMI cable, and try connecting that way.  

I haven't tried this in linux, but its how I connect my LCDtv to my windows box.  Just an idea.

---

