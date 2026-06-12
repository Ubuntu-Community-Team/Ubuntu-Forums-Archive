---
title: "star3 touchpad"
date: 2010-09-12
forum: System76 Support
---

### Post by tanderson on 2010-09-12
I have star3 netbook and there doesn't seem to be any app to adjust touchpad. There is no tab underneath mouse as described in other threads. Am I missing something. If i have to I will get into xinput.

xinput list-props
Device 'FSPPS/2 Sentelic FingerSensingPad':
	Device Enabled (134):	1
	Device Accel Profile (251):	0
	Device Accel Constant Deceleration (252):	1.000000
	Device Accel Adaptive Deceleration (254):	1.000000
	Device Accel Velocity Scaling (255):	10.000000
	Evdev Reopen Attempts (249):	10
	Evdev Axis Inversion (256):	0, 0
	Evdev Axes Swap (258):	0
	Axis Labels (259):	"Rel X" (142), "Rel Y" (143)
	Button Labels (260):	"Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141), "Button Unknown" (250), "Button Unknown" (250), "Button Forward" (407), "Button Back" (408), "Button Unknown" (250), "Button Unknown" (250), "Button Unknown" (250), "Button Unknown" (250)
	Evdev Middle Button Emulation (261):	2
	Evdev Middle Button Timeout (262):	50
	Evdev Wheel Emulation (263):	0
	Evdev Wheel Emulation Axes (264):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (265):	10
	Evdev Wheel Emulation Timeout (266):	200
	Evdev Wheel Emulation Button (267):	4
	Evdev Drag Lock Buttons (268):	0

---

### Post by marshmallow1304 on 2010-09-13
Try gpointing-device-settings [[apturl]("apt://gpointing-device-settings")].

---

### Post by isantop on 2010-09-13
Actually, the Serval and the Starling share the same touchpad. There is a configuration utility, with instructions for installing it on the Serval Page on out knowledge base. I've added the tutorial to the Starling's page as well:

[http://knowledge76.com/index.php/Star3](http://knowledge76.com/index.php/Star3)

---

### Post by tanderson on 2010-09-13
thank-you for the help. Probably what I needed most was to know how the touch pad worked.

---

