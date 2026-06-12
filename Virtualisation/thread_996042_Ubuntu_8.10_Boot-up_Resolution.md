---
title: "Ubuntu 8.10 Boot-up Resolution"
date: 2008-11-28
forum: Virtualisation
---

### Post by chrini on 2008-11-28
So I have tried pretty much every suggestion in this forum to get my boot-up (login menu) resolution to be the same as my default resolution, and nothing has fixed it yet.

I am running Ubuntu 8.10 within VMware Player on my XP machine. 

Let me know if you need any other information. I've attached my xorg.conf file (after being edited a few times to try and fix the problem) as well as a screenshot of what my login menu looks like.

Thanks in advance!

xorg.conf

> Section "InputDevice"
  Driver "vmmouse"
  Identifier "VMware Mouse"
  Option "Buttons" "5"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "IMPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "vmware"
EndSection

Section "Monitor"
Identifier "Monitor0"
HorizSync 1.0 - 10000.0
VertRefresh 1.0 - 10000.0
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
	Depth	24
	Virtual	1280 800				
Modes	"1280x800@60"	"1280x720@60"	"1280x800@75"	"1280x768@60"	"1280x768@75"	"1280x854"	"1280x720@50"	"1152x768@54"	"800x600@60"	"1440x900@75"	"800x600@85"	"800x600@75"	"1600x1024@60"	"800x600@72"	"1680x1050@60"	"800x600@56"	"1680x1050@75"	"720x400@85"	"1920x1200@75"	"640x350@85"	"1920x1200@60"	"640x400@85"
	EndSubSection



EndSection

---

### Post by chrini on 2008-12-01
Anyone got any suggestions? Please Help!!!!

---

### Post by wiresquire on 2008-12-03
The login screen (and ubuntu splash screen) are not directly related to the xorg settings.

I fixed mine, or at least made it look better, by using the vga boot parameter. Basically you need to edit /boot/grub/menu.list and add vga=XXX to the end of the kernel line, where XXX is the correct graphics resolution and mode.

You will likely need to experiment and reboot with several different modes.

See [http://forums.fedoraforum.org/archive/index.php/t-170490.html](http://forums.fedoraforum.org/archive/index.php/t-170490.html) for some suggestions on which numbers might work best for you.

hth
ws

Edit: Also, the resolutions will be determined by the virtual graphics card in your guest VM - not by the resolutions of your real graphics card. This is probably the real reason that your resolution in the screenshot looks funny. The modes you have in your xorg.conf (eg widescreen) are unlikely to be supported natively by the virtual graphics card. Try something 'safe' like 1280x1024 or 800x600

---

### Post by karlatsaic on 2008-12-04
> **chrini said:**
> Anyone got any suggestions? Please Help!!!!
hmm...The first time I brought up the 8.10 image and it was too small, I just went into System/Preferences and found a setting which gave me the whole screen at the correct aspect ratio - in my case that was 16:9, but that probably won't help you. Once I set it that way, it comes up that size every time I fire up my ubuntu 8.10 image under vista.

---

