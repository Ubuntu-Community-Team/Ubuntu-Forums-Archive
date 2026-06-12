---
title: "missing sensitivity adjust on Elantech touchpad"
date: 2015-08-05
forum: Ubuntu Development Version
---

### Post by donbowman on 2015-08-05
On vivid, i was able to set the sensitivity of my Elantech touchpad.
On wily, I am not. 
At first I had no touchpad support, then i installed xserver-xorg-input-libinput, and I had the basics. But its missing the more advanced features (they are greyed out). The multitouch does work, and the scrolling does too, but the speed / jitter sensitivity cannot be controlled (making it hard to use).

I tried the fix from [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all") (even though the symptoms don't match exactly), but it doesn't build with the 4.1 kernel, giving
```
cypress_ps2.c:570:2: error: too few arguments to function ‘input_mt_assign_slots’
  input_mt_assign_slots(input, slots, pos, n);
```

The machine is a Samsung series 9 (n900x3c). The [Xorg.0.log is here]("https://gist.githubusercontent.com/donbowman/d19d81e8c1a96ce5a970/raw/8d2c9085cb9b1c8f94f90573db05edac76f158d1/Xorg.0.log").

Does anyone have any suggestion for what I should be seeing? I'd like to be able to adjust the sensitivity.

```
[    2.136119] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x361f04)[    2.151159] psmouse serio1: elantech: Synaptics capabilities query result 0x40, 0x14, 0x0d.
[    2.226863] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input5

$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

$ dpkg -l |grep xorg-input
ii  xserver-xorg-input-all                        1:7.7+7ubuntu4                             amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                      1:2.9.2-1ubuntu1                           amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-libinput                   0.11.0-1                                   amd64        X.Org X server -- libinput input driver
ii  xserver-xorg-input-mouse                      1:1.9.1-1                                  amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics                  1.8.2-1ubuntu1                             amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                    1:13.1.0-0ubuntu1                          amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                      1:0.30.0-0ubuntu1                          amd64        X.Org X server -- Wacom input driver

$ xinput list-props "ETPS/2 Elantech Touchpad"
Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (138):	1
	Coordinate Transformation Matrix (140):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Tapping Enabled (271):	1
	libinput Tapping Enabled Default (272):	0
	libinput Accel Speed (273):	0.000000
	libinput Accel Speed Default (274):	0.000000
	libinput Natural Scrolling Enabled (275):	0
	libinput Natural Scrolling Enabled Default (276):	0
	libinput Send Events Modes Available (256):	1, 1
	libinput Send Events Mode Enabled (257):	0, 0
	libinput Send Events Mode Enabled Default (258):	0, 0
	libinput Left Handed Enabled (277):	0
	libinput Left Handed Enabled Default (278):	0
	libinput Scroll Methods Available (279):	1, 0, 0
	libinput Scroll Method Enabled (280):	1, 0, 0
	libinput Scroll Method Enabled Default (281):	1, 0, 0
	libinput Click Methods Available (282):	1, 1
	libinput Click Method Enabled (283):	1, 0
	libinput Click Method Enabled Default (284):	1, 0
	Device Node (259):	"/dev/input/event5"
	Device Product ID (260):	2, 14





```

---

