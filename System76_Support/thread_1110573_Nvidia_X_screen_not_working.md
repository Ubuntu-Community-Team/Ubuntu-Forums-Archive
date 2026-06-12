---
title: "Nvidia X screen not working"
date: 2009-03-29
forum: System76 Support
---

### Post by chez17 on 2009-03-29
Pangolin Panp4n, Intrepid 64 bit

I am trying to set up Nvidia to run two separate x screens. I got a new wide screen ASUS monitor that has an HDMI in. I am using the Pangolin's HDMI out and while the dual set up seems to work, the secondary monitor can't handle the full 1920x1080 resolution. Part of the screen is just black and while I can move my mouse over the black, I can't drag an application over it. This black space is on the right and bottom of the monitor. If I change the resolution on the second monitor and lower it, it works fine. Does anyone know of any issues that nvidia might have with full 1920x1080 resolution on a second x screen? Any ideas on how to fix this?

Just in case, here is the xorg.cong I am using

```

Section "ServerLayout"
Identifier     "Default Layout"
Screen         "Screen0" 0 0
Screen         "Screen1" RightOf "Screen0"
InputDevice    "Keyboard0" "CoreKeyboard"
InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
Load           "glx"
EndSection

Section "InputDevice"

# generated from default
Identifier     "Keyboard0"
Driver         "keyboard"
EndSection

Section "InputDevice"

# generated from default
Identifier     "Mouse0"
Driver         "mouse"
Option         "Protocol" "auto"
Option         "Device" "/dev/psaux"
Option         "Emulate3Buttons" "no"
Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "CMO"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "ACI ASUS VH222H"
	HorizSync       30.0 - 85.0
	VertRefresh     55.0 - 75.0
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9300M GS"
	BusID          "PCI:1:0:0"
	Screen          0
EndSection

Section "Device"
	Identifier     "Device1"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9300M GS"
	BusID          "PCI:1:0:0"
	Screen          1
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option				 "TwinView" "0"
	Option         "NoLogo" "True"
		SubSection     "Display"
			Depth       24
			Modes      "nvidia-auto-select"
		EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen1"
	Device         "Device1"
	Monitor        "Monitor1"
	DefaultDepth    24
	Option				 "TwinView" "0"
	Option         "NoLogo" "True"
		SubSection     "Display"
			Depth       24
			Modes      "nvidia-auto-select"
		EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by Lee_Machine on 2009-03-29
I have the same problem with the Pangoline hooked up to my Panasonic Plasma TV. It wasn't too big of a deal because I just use it to watch movie in full-screen and it goes away. 

When testing Jaunty beta I dont get the same issue. I dont know if I has to do with the work they did on this problem, or the new nvidia driver.

Either way a fix did come.....in the new release at least.

---

### Post by chez17 on 2009-03-29
I got the full resolution by switching the new monitor to screen 0 and using the laptop monitor as the second screen. Since this is not how I want it set up, any advice on getting the second x screen to run in 1920x1080 would still be most appreciated. In this new setup, the big issue I am having now is that the gnome panels don't work. I can't click on a menu or launcher. If I use my key commands that I set up in gconf-editor, then the programs run fine. Why would the panels stop working? Windows don't even show up on the window list.

---

