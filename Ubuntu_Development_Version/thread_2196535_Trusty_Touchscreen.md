---
title: "Trusty Touchscreen?"
date: 2013-12-30
forum: Ubuntu Development Version
---

### Post by akgrant on 2013-12-30
Hi,


Santa kindly delivered a new Dell XPS13 for Christmas, which appears to include a touch screen as shown in the two commands below.


Should I expect to be able to use the touchscreen in Trusty Tahr?  Looking around in google was inconclusive, I saw some references to using a touchscreen and needing to have the (then) latest kernel, but nothing that included any instructions on how to activate the touch capabilities.


For the record, the output below has the touchscreen module (i2c_hid) blacklisted so that the touchpad is correctly recognised.


Thanks,
Alistair




$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SYNAPTICS Synaptics Large Touch Screen  	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4013	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]




$ xinput --list-props 9
Device 'SYNAPTICS Synaptics Large Touch Screen':
	Device Enabled (134):	1
	Coordinate Transformation Matrix (136):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Device Product ID (251):	1739, 2808
	Device Node (252):	"/dev/input/event5"
	Evdev Axis Inversion (263):	0, 0
	Evdev Axis Calibration (264):	<no items>
	Evdev Axes Swap (265):	0
	Axis Labels (266):	"Abs MT Position X" (257), "Abs MT Position Y" (258), "None" (0), "None" (0)
	Button Labels (267):	"Button Unknown" (254), "Button Unknown" (254), "Button Unknown" (254), "Button Wheel Up" (140), "Button Wheel Down" (141)
	Evdev Middle Button Emulation (268):	0
	Evdev Middle Button Timeout (269):	50
	Evdev Third Button Emulation (270):	0
	Evdev Third Button Emulation Timeout (271):	1000
	Evdev Third Button Emulation Button (272):	3
	Evdev Third Button Emulation Threshold (273):	20
	Evdev Wheel Emulation (274):	0
	Evdev Wheel Emulation Axes (275):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (276):	10
	Evdev Wheel Emulation Timeout (277):	200
	Evdev Wheel Emulation Button (278):	4
	Evdev Drag Lock Buttons (279):	0

---

### Post by akgrant on 2013-12-30
OK, that's embarrassing...  As soon as I post this my 3yr old comes along and uses the touch screen.  Naturally I hadn't tried if after blacklisting i2c_hid, sigh...

Sorry for the noise,
Alistair

---

### Post by grahammechanical on 2013-12-30
So, Trusty works with touchscreens? That is interesting news. I would have said that we would need to wait until there was closer convergence between the Ubuntu mobile code and the Ubuntu desktop code.

Does the Screen Display utility in System Settings give an indication that it knows that the screen is a touch screen? How does it list this screen?

Regards.

---

### Post by zika on 2013-12-30
> **akgrant said:**
> OK, that's embarrassing...  As soon as I post this my 3yr old comes along and uses the touch screen.  Naturally I hadn't tried if after blacklisting i2c_hid, sigh...

Sorry for the noise,
AlistairIt is not embarassing at all... ;) This world stands upon kids like Yours. Please give him/her a big loud kiss on my behalf on both cheeks...
I wish him/her and You all peace, love and happiness in 2014. This made my day, I'm smiling for hours...

---

### Post by grahammechanical on 2013-12-30
It would be really embarrassing if it was the cat and not a child that did it. :)

---

### Post by akgrant on 2013-12-30
> **grahammechanical said:**
> 
Does the Screen Display utility in System Settings give an indication that it knows that the screen is a touch screen? How does it list this screen?


The Screen Display utility in the System Settings doesn't give any indication at all that it is a touch screen.  It's listed just as "Built-in Display" with the usual controls (On/Off, Mirror, Resolution, Rotation, Launcher Placement, Sticky Edges).

---

### Post by akgrant on 2013-12-30
> **zika said:**
> Please give him/her a big loud kiss on my behalf on both cheeks...

Done.

> **grahammechanical said:**
> It would be really embarrassing if it was the cat and not a child that did it. :)

Just as well we don't have a cat... 

:p

---

