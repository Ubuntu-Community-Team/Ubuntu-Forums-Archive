---
title: "Does touchscreen work on moblin or MeeGO ?"
date: 2010-07-21
forum: Ubuntu Moblin Remix
---

### Post by darkforester67 on 2010-07-21
Im thinking of buying a Asus EEE T91-BLK020X Touchscreen Netbook and get ubuntu moblin or MeeGO >.< does it have any support for touch screen? :popcorn:

---

### Post by cariboo on 2010-07-22
Ubuntu Moblin is no longer available, use the UNE, it supports touch screens.

---

### Post by darkforester67 on 2010-07-25
> **cariboo907 said:**
> Ubuntu Moblin is no longer available, use the UNE, it supports touch screens.

Does Meego support touchscreen tho >.,<?

---

### Post by fleton on 2010-08-01
Yes, Meego currently has support for touchscreens.

---

### Post by joshruehlig on 2010-08-07
Using a self installed resistive eGalax touchscreen on a Dell Mini 9 I got the touchscreen reacting on both Meego and ubuntu netbook remix 10.04. On both anytouch goes to the top left corner.

On ubuntu 10.04 all I had to do was blacklist usbtouchscreen module, download xserver-xorg-input-evtouch, put a config file in /usr/lib/X11/xorg.conf.d and edit the file a bit to perfect the calibration.

1. sudo gedit /etc/modprobe.d/blacklist.conf
 add "blacklist usbtouchscreen" to the end of the file
2. sudo apt-get install xserver-xorg-input-evtouch
3. sudo gedit /usr/lib/X11/xorg.conf.d/11-touchkit.conf
put this in the file
__________
Section "InputClass"
	Identifier "Touchkit Touch"
	MatchIsTablet	"on"
	MatchDevicePath "/dev/input/event*"
	Driver 	"evtouch"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emultate3Timeout"	"50"
	Option	"SendCoreEvents"	"On"
	Option	"TapTimer"		"200"
	Option	"LongTouchTimer"	"400"
	Option	"MinX"			"23"
	Option	"MinY"			"25"
	Option	"MaxX"			"4087"
	Option	"MaxY"			"4043"
EndSection
__________
4. Change values as needed, each time restarting to implement changes (though a x-org restart may do).

NOTE - this may not work for you depending on your touchscreen
(This info was taken from [http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877))
--------------------------------------------------------------
For meego I tried this but it didn't seem to work but I will experiment with this and post if I get it to work later

---

