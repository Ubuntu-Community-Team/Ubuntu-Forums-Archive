---
title: "ESXI Passthrough Setup"
date: 2015-06-24
forum: Virtualisation
---

### Post by aajvs99 on 2015-06-24
This is a quick guide for anyone setting up a passthrough box using ESXI as the host Hypervisor. Here is quick overview of my setup:

Base HP Z800 Workstation
2 - nVidia Quadro 3800 (1 for Windows 1 for Xubuntu 15.04)
1 - 240GB Intel SSD (VM Storage)
4 - 2TB HGST 3.5" Drives

VM Loadout:
1 Windows 7 Installation
1 Xubuntu Installation
1 FreeNAS Installation

The 4 2TB drives are configured in RAID 10 and given to FreeNAS for file storage between Windows and Xubuntu. FreeNAS runs in the background is typically not touched.

Windows installs without a problem with passthrough. Most of my issues were with Xubuntu seeing the GPU properly and displaying video properly. 

The initial install goes fine and I can access the VM through either VMWare Workstation/Fusion or vSphere Console. However, the initial install does not see the secondary display causing a problem. To make this default to my monitor off of the GPU it took a few steps. 

1. Install nVidia Drivers ( I am not going to detail this at all. There are plenty of guides)
2. Return to a TTY screen CTRL+ALT+F1
3. Login
4. Stop lightdm 
```
sudo service lightdm stop
```
5. Reconfigure X Server - this will generate a new xorg.conf file that we need to modify.
```
sudo Xorg -configure
``` 

The xorg.conf file that it creates will be placed in your home directory and called xorg.conf.new it should look similar to:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	BusID       "PCI:11:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "HWcursor"           	# [<bool>]
        #Option     "Xinerama"           	# [<bool>]
        #Option     "StaticXinerama"     	# <str>
        #Option     "GuiLayout"          	# <str>
        #Option     "AddDefaultMode"     	# [<bool>]
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "DirectPresents"     	# [<bool>]
        #Option     "HWPresents"         	# [<bool>]
        #Option     "RenderCheck"        	# [<bool>]
	Identifier  "Card1"
	Driver      "vmware"
	BusID       "PCI:0:15:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

As you see it pre-programs two screens for dual monitors Screen0 is the screen we want to keep as it is associated with Card0 which is our GPU. Your setup may vary so pay attention to what Device is associated with what screen. In my setup I removed everything related to my second monitor as the second monitor is the standard VMWare graphics card which I do not want to use. I edited the xorg.conf.new file to look like:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	BusID       "PCI:11:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



```

Save it in your home directory as "xorg.conf.new2". We now need to move this into the Xorg folder. Run the following command:
```
sudo cp xorg.conf.new2 /etc/X11/xorg.conf
```

To test your configuration run this command:
```
sudo service lightdm start
```

You should be prompted with a login screen on your primary display. I then rebooted my setup to ensure that all was configured properly.

Any questions feel free to send me a message or reply!

---

