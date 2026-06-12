---
title: "ummm fix out of range problem monitor"
date: 2008-05-09
forum: Ubuntu Brainstorm
---

### Post by marine63 on 2008-05-09
hi... everytime i install ubuntu i always get the same problem of getting the black screen and "out of range"... is there anything ya'll can do about it or are ya'll working on it... i think this should be high priority b/c what good is a operating system if you cant use it... 
also, is there a temporary solution to this problem thx
and it would be nice to know exactly what is the problem...
my video card is geforce 8800 gts and x2gen mw19r (crap) monitor 1440x960 and 70 refresh rate max
I can get out my old hp m90 crt and don't have any problems but i look at the refresh rate is at 85 way beyond my lcd abilities...

---

### Post by bb002 on 2008-05-14
Ah yes I have this monitor too.

The EDID info for this monitor has a typo in it for the 1440x900 resolution. Took me forever to figure that one out. Which causes Xorg to freak out a bit. For whatever reason windows is unaffected by this typo, probably another place that windows fails to follow standards causing OSes that do to suffer the fallout. :P

.....crap. synergy isn't wanting to copy-n-paste atm. give me a minute to post this, switch stations, and edit my post...



[EDIT]

Here is what my monitor and screen sections look like in xorg now to get my monitor working.
```

Section "Monitor"
	Identifier	"Generic Monitor"
	# Is really a X2Gen monitor but claims to be a "KT@ KT-191W" in the EDID.
	VendorName	"KT@"
	ModelName	"KT-191W"
	Option		"DPMS"
	Horizsync	30-82
	Vertrefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV40 [GeForce 6800]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"metamodes" "1440x900_75 +0+0; 1024x768 +0+0; 800x600 +0+0"
# Commented most of the following because of the above metamode. Still get "Out of Sync" if I don't. >_>
#	SubSection "Display"
#		Depth	16
#		Modes		"1440x900"	"1024x768"	"800x600"
#	EndSubSection
	SubSection "Display"
		Depth	24
#		Modes		"1440x900"	"1024x768"	"800x600"
	EndSubSection
EndSection


```


And here is the parse-edid output of my monitor for those that really want to know and those that want to fix this issue in the future.
My monitor is a **X2gen mw19r 19" monitor** but identifies itself as a "KT@ KT-191W" in the EDID data. 
 ```
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "KT-191W"
	VendorName "KT@"
	ModelName "KT-191W"
	# Block type: 2:0 3:fd
	HorizSync 30-82
	VertRefresh 50-76
	# Max dot clock (video bandwidth) 170 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1440x900"	# vfreq 77.875Hz, hfreq 73.125kHz
		DotClock	146.250000
		HTimings	1440 1544 1720 2000
		VTimings	900 903 909 939
		Flags	"+HSync" "-VSync"
	EndMode
	Mode 	"640x350"	# vfreq 70.072Hz, hfreq 31.462kHz
		DotClock	25.170000
		HTimings	640 656 752 800
		VTimings	350 387 389 449
		Flags	"-HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

```
the monitor supports far more resolutions than that but notice the 1440x900 one. the vertrefresh range of the monitor is 50-76 but the 1440x900 claims 77.875Hz when it should really be either 74.98Hz (75Hz) or 60Hz.

I've also attached the EDID dump that I got through nvidia-settings. The get-edid program complained about unsupported calls while dumping the EDID. might have been because Xorg was running...

---

### Post by me0262 on 2008-07-31
Thanks, I've been looking for this info since my monitor started doing the same thing 3 months ago.

Oddly, it only started happening when I switched to an updated Gentoo kernel.

Unfortunately the company has been out of business since November 2007, so we can't ask them for an updated EDID file.
We could try finding someone who has this monitor and doesn't have this problem (needle in a haystack, most of these users are using Windows and unaware), or we could try hacking it outselves (anyone know how to edit an EDID?).
I'm going to try this fixed xorg.conf in the meantime.

And yes, even the nvidia driver knows about the problem.
(WW) NVIDIA(0): The EDID for KT@ KT-191W (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "1440x900" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (50.000-76.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (77.9 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1440x900".
(WW) NVIDIA(0): No valid modes for "1440x900@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"

---

### Post by cszikszoy on 2008-08-02
You would probably get more help with this problem by posting a bug in Launchpad.  Bug fixes are generally _not_ ideas, because that's pretty much the point, is to fix the bugs.

---

### Post by Bodsda on 2008-08-11
This is not really a bug, more xorg not being able to detect your screen properly. 

When you get an out of range/sync error the usual fix is to find out what your monitors 'HorizSync' and 'VertRefresh' rates are and place them in the 'Monitor' section in /etc/X11/xorg.conf

---

