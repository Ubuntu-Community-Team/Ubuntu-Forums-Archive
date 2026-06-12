---
title: "Can anyone help: need correct reolution and fullscreen for xp-guest in vmware-server?"
date: 2007-07-04
forum: Virtualisation
---

### Post by fsando on 2007-07-04
I've installed xp as a guest in vmware-server (version 1.0.3).
I have 2 problems (that may be related)
1) The native resolution of my laptop-screen doesn't show up in xp (I've earlier seen a solution to this - tried it but it doesn't work anymore).
How do I make xp-guest acknowledge my screen resolutions (I know abourt 'autofit guest' which is not the same I guess).
2) When I try to get fullscreen vmware responds with an error:
> 
Unable to find an appropriate host video mode
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.
Why is vmware saying this?
I have all kinds of resolutions in xorg.conf. So either vmware is wrong here or it has succeded in asking for some strange resolution not in xorg.conf.

---

### Post by dachinster on 2007-07-22
I have a similar error.
I am using Ubuntu Feisty 7.04
I have vmware server console 1.03 build 44356
My desktop resolution is 1440x900

My guest operating system does not see this resolution and changing it gives the following error:

> Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.
Failed to switch to full screen mode.

I tried following this guide:
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1003](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1003)

i did up to step 6 and then from step 10 onwards but i did not see the resolution displayed.

can anyone assist?

---

### Post by dachinster on 2007-07-22
bump

---

### Post by dachinster on 2007-07-23
anyone?
anything?

---

### Post by anewguy on 2007-07-23
Did you install Vm Tools to the guest (Windows) operating system virtual machine?

---

### Post by dachinster on 2007-07-23
yes i do.
the guest machine has 11 existing resolutions ranging from 800x600 to  2560x1600 (or something like that)
just not seeing mine (1440x900)

---

### Post by jonathanmotes on 2007-08-03
I also have this problem! XP is guest on Ubuntu host with VM tools installed. I have a HP dv9000 series laptop - native resolution of 1440 x 900 pixels - but it doesn't show up in the XP display resolutions list.

Anyone know how to fix this? 

As a side note, when I installed Ubuntu it didn't detect the correct resolution either, but the nVidia driver fixed that problem....is it possible that VMware is looking at the original xorg settings or something?

---

### Post by OneSeventeen on 2007-08-04
I am having the same issues with my HP Pavilion zv6000 laptop.

I was hoping to use this for a presentation on free software (windows and linux) and this would make for an awesome presentation.

(Especially if I can use the compiz cube to switch between windows and linux! :) )

I'll keep looking, and will post back if I figure it out.

---

### Post by anewguy on 2007-08-04
I've never tried changing resolutions in Windows while it is running in a vm.  However, since VMWare-Server is using its' own video "device" and driver, I could see not being able to get the higher resolution you want.  You might want to post on the vmware forum and see if someone can tell you the limitations of the virtual video device and driver.:)

---

### Post by buzzbo on 2007-12-16
yet another bump.  This thread came up on a search.

I've also got the HP dv9000 laptop with nVidia geforce 8500, and native 1440x900, running gutsy (host).  The native resolution is not listed in winXP (guest) display properties after installing vmware tools.

fwiw, I've run openSuse, Fedora, and ubuntu as guest and I have no problem getting the full 1440x900.

Has anybody found the solution to this?

Thanks,
Buzz

---

### Post by buzzbo on 2007-12-16
OK I thought I'd post a follow-up.  

I [found this thread]("http://ubuntuforums.org/showthread.php?t=300968"), which worked for me, and I am now getting 1440x900 in WinXP.

Buzz

---

### Post by MonsterMaxx on 2008-01-14
yet another bump, this came up in a search. XP won't run fullscreen for me either.

I've done the above link and it didn't work.

I've also done the matching resolution thing. After some wrestling I was able to get Fedora7 running as a client by  running vmware-config-tools.pl and set the res in there.


is there maybe a vm setting somewhere that needs editing to point to xorg.conf instead of XF86Config?


I have found a workaround, if 'Quick Switch' works for you. (never had probs with it.)

Go ahead and start XPclient. Then go into VM's >View and uncheck tabs, status bar, turn off icons etc, then when everything is off hit the 'Fit Guest Now'. You'll still have access to VM via a hidden panel.

On my system that's as close to XP full screen as close can get. Really cool part is a ctrl+alt double tap releases me from XP and I'm back in linux.

---

### Post by chadjohnson on 2008-01-14
Another solution that might work...
```

DISPLAY=:0 vmware

```

To make your shortcuts work like this, change their command to
```

env DISPLAY=:0 vmware

```

---

### Post by brett611 on 2008-03-18
Try this link.  The instrux look very straightforward and make sense conceptually

[http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html](http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html)

---

### Post by MonsterMaxx on 2008-03-18
I had the same problem. 
Assuming you are using Nvidia drivers, they do not setup the xorg right for vmware. You need to make your xorg.conf include the display modes.

Here's mine, it works, XP, full screen, etc.

It needs the **SubSection "Display"** entry

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:10:32 PST 2007
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007
# Xorg configuration created by system-config-display
# Section "Module"
#    Load           "glx"
# EndSection

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "Emulate3Buttons" "no"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "CRT-0"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    30.0 - 110.0
	VertRefresh  50.0 - 150.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Unknown"
	ModelName    "TV-0"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    28.0 - 33.0
	VertRefresh  43.0 - 72.0
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 7800 GS"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 7800 GS"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1280x1024 +0+0"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "TwinViewXineramaInfoOrder" "CRT-0"
	Option	    "metamodes" "CRT: 1280x1024_85 +0+0; CRT: 1280x1024 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "TV: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection


```

Hope that helps.

---

