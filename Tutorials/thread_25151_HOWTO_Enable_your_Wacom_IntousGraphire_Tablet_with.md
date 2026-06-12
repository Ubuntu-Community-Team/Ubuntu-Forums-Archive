---
title: "HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity"
date: 2005-04-09
forum: Tutorials
---

### Post by MetalMusicAddict on 2005-04-09
This HOW-TO is written for USB Wacom Tablet devices.

Some links for reference:
[Ubuntu Tablet Wiki Page](http://www.ubuntulinux.org/wiki/WacomTabletIssue) 
[Wacom Help Page](http://linuxwacom.sourceforge.net/index.php/howto/main)
Once you have some success these links will make more sense. Theres TONS of good info that will make working in The GIMP better.


**1.** Connect your USB Wacom Tablet device


**2.** Install "wacom-tools". This is need to set the event in your xorg.conf.

In a terminal:
```
sudo apt-get install wacom-tools
```

Or find "wacom-tools" in Synaptic.

**3.** Edit this below Section **"InputDevice"** under the **"Configured Mouse"**. Make sure you use the right **"Device"** based on how your pad is connected. ie: USB or serial.
```

[SIZE="1"]Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          **#SERIAL ONLY**
  Option        "Device"        "/dev/input/wacom"   **#USB ONLY**
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  **#USB ONLY**
  Option        "ForceDevice"   "ISDV4"               **#Tablet PC ONLY**
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          **#SERIAL ONLY**
  Option        "Device"        "/dev/input/wacom"   **#USB ONLY**
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  **#USB ONLY**
  Option        "ForceDevice"   "ISDV4"               **#Tablet PC ONLY**
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          **#SERIAL ONLY**
  Option        "Device"        "/dev/input/wacom"  ** #USB ONLY**
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  **#USB ONLY**
  Option        "ForceDevice"   "ISDV4"              ** #Tablet PC ONLY**
EndSection[/SIZE]

```

*If* you have a Intuos3 or Cintiq 21UX add this section. (Untested by me)

```
[SIZE="1"]Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyS0"          **#SERIAL ONLY**
  Option        "Device"        "/dev/input/wacom"   **#USB ONLY**
  Option        "Type"          "pad"
  Option        "USB"           "on"                  **#USB ONLY**
EndSection[/SIZE]
```
**4.** Add these lines to the Section **"ServerLayout"**.
```

[COLOR="SlateGray"][SIZE="1"]Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"[/COLOR]
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    **#For non-LCD tablets only**
        InputDevice    "pad"   **#For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event[/SIZE]**
[COLOR="SlateGray"]EndSection[/COLOR]

```
_*NOTE*_
You can adjust the pressure curves on your tablet. Just adjust the **"PressCurve"** line at bottom of the stylus section.

Example:
```
[SIZE="1"]Option "PressCurve" "50,0,100,50"[/SIZE]
```
This edit will make the drawn lines appear lighter. you can still get really dark lines, you just have to press harder. Makes it easier to make really light or faint changes. -Thanx graigsmith. ;)


**5.** Reboot or restart X with ctrl-alt-backspace and launch The GIMP

**6.**Enable the tablet in applications.

**_[SIZE="3"]The GIMP[/SIZE]_**
- **File**-> **Preferences**-> **Input Devices**-> "Configure Extended Input Devices".
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".

Now you should have pressure sensitivity in The GIMP. :)

Also, a useability note with Gimp:
Each input device (stylus,cursor,eraser) has a completely different set of attributes in Gimp, and in theory, you can even assign a unique serial number to different pens to get even more granularity. You will experience this when you try to use your eraser for the first time. Rather than selecting the eraser tool, you get the rectangle selection tool instead. This is by design, believe it or not. Gimp does not care that its an eraser, just that it's not the pen you were just using. If you choose the eraser tool now, it will remember that for the next time you try to use it. On the plus side, you can set the eraser to be anything, including the Airbrush tool or Clone tool.
-Taken from [The Wacom Help Page.](http://linuxwacom.sourceforge.net/index.php/howto/main)

**_[SIZE="3"]Inkscape[/SIZE]_**
- **File**-> "Input Devices...".
[SIZE="1"](The dialog is the same as The GIMP)[/SIZE]
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".

**_[SIZE="3"]Krita[/SIZE]_**
- **Settings**-> "Configure Krita..." then click on the "Tablet" icon.
- Check the "Enable" boxes for all 3 Devices.

Do you know of more apps that use a tablet?

If anyone has info to make this better let me know. ;)

---

### Post by graigsmith on 2005-05-10
Step 2 is unnecessary if you replace it with this easier way to get your device.

```
sudo apt-get install wacom-tools
```

After installing wacom-tools and following a reboot, you should have a /dev/input/wacom device name, that should correctly point to your tablet. (haven't tested this with a serial tablet)

Now all you have to do is just rename all your wacom devices, from /dev/input/event0 to /dev/input/wacom

Also if you run into problems make sure that you didn't include the commented things in the xorg file.

```
Option        "Device"        "/dev/input/event0"   #USB ONLY
```
is incorrect, and probably wont work right. just delete the #usb only.

---

### Post by Staesys on 2005-05-15
Thanks very much for this!

Mine is on event3, btw.

:-)

-Paul

---

### Post by DirtDawg on 2005-06-11
The link labeled 'wacom help page' goes to Microsoft.com(!!)

---

### Post by MetalMusicAddict on 2005-06-12
Wow. So does the link to the original thread.  :-?

---

### Post by c4pp4 on 2005-08-07
*Thank you very much.*

---

### Post by Stormy Eyes on 2005-08-08
[QUOTE=MetalMusicAddict]I've done this on Hoary (Pre and Final) with a Graphire 2. I have confirmation it works on Warty.[/QUOTE]

Thanks. I had bought a Wacom Graphire for my wife when she came from Australia to move in with me last August, but I never was able to make the damned thing work until you posted your HOWTO.

---

### Post by grendelkhan on 2005-08-08
My tablet's an older serial port one. what would I put in place of /dev/usb? /dev/ttyS0 ?

---

### Post by Stormy Eyes on 2005-08-08
[QUOTE=grendelkhan]My tablet's an older serial port one. what would I put in place of /dev/usb? /dev/ttyS0 ?[/QUOTE]

Probably. If you already have a serial modem hooked up as well, then try /dev/ttyS1 too.

---

### Post by Waqas on 2005-09-11
A noob question here if you dont mind..:-

I downloaded the *WacomLinux-0.6.8.tar.bz2* driver. So, how to install it. Im not sure whats the first step after downloaded the driver.. can you walk me through this briefly please??  O:) 

I think you guys edited the xorg.conf file after installing the driver, right??  :-?

---

### Post by Sharebear on 2005-09-12
[QUOTE=Waqas]I think you guys edited the xorg.conf file after installing the driver, right??  :-?[/QUOTE]

Can't say for certain as I haven't tried this yet (batteries just ran out on my wireless mouse so desperately searching for the above info, thanks), but you shouldn't have to install anything on Hoary.

There is a wacom driver built into the the X.org distributed with Hoary, however it could be worthwhile someone checking what will happen when we move to R7 as the wacom driver will no longer be bundled in[http://wiki.x.org/wiki/DeprecatedInX11R7](http://wiki.x.org/wiki/DeprecatedInX11R7) . Someone needs to ensure the linuxwacom version of the driver becomes part of the ubuntu distribution too, in order for support to continue.

HTH

Jon

---

### Post by graigsmith on 2005-09-13
[QUOTE=Sharebear]Can't say for certain as I haven't tried this yet (batteries just ran out on my wireless mouse so desperately searching for the above info, thanks), but you shouldn't have to install anything on Hoary.

There is a wacom driver built into the the X.org distributed with Hoary, however it could be worthwhile someone checking what will happen when we move to R7 as the wacom driver will no longer be bundled in[http://wiki.x.org/wiki/DeprecatedInX11R7](http://wiki.x.org/wiki/DeprecatedInX11R7) . Someone needs to ensure the linuxwacom version of the driver becomes part of the ubuntu distribution too, in order for support to continue.

HTH

Jon[/QUOTE]
 no, i think that ubuntu already has the driver. isn't it included in the kernel?

---

### Post by Sharebear on 2005-09-13
[QUOTE=graigsmith]no, i think that ubuntu already has the driver. isn't it included in the kernel?[/QUOTE]
Personally I haven't got a clue on that so it could be...but for the benefit of Waqas I can confirm that nothing extra needs to be installed on top of a standard Hoary install to get the above instructions to work although as I use the Wacom mouse as my primary mouse for general computer use I added  Option "Mode" "Relative" into the cursor InputDevice section to make it usable.

Jon

---

### Post by Waqas on 2005-09-13
Fortunately, I managed to make my Wacom tablet works. Its all my fault, I should've read the first post in this thread properly. I deleted/replaced the mouse configuration at first try and it was a chaos..

So, for me, I didnt even installed the driver. What I need to do was just adjust the parameter for /etc/X11/xorg.conf. Add lines as explained, and dont forget to adjust..

 >  Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/[color=Red]**mouse1**[/color]"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection   

..if your mouse is PS/2 (default was [color=Red]mice[/color] for me). If not, GIMP will freeze after a while.

Thanks to all of you who generously wrote long HOWTOs.. :-P

---

### Post by coz on 2005-10-04
Hello,
 noob here.
 I have another thread going on with another fellow about the nvidia drivers in breezy. This one is about the wacom driver/tools
 I have a graphire 2 and an intuos3. I am using the graphire on the breezy machine. But being a noob I need a blow by blow on how to configure this for my machine. ANY help would be well appreciated. Right now the pen and mouse work but I have to fumble with it because it doesn't always center properly.
 Thanks
 Coz

---

### Post by cosimo on 2005-10-06
Oh Yes,
  Everything I have read about installing the wacom drivers on breezy are nonsense to my ears. I have read everything here, and that wiki place and nothing helps. I have no idea hoe to get from step c to h, and that's what is all sounds like to me. You all use the same a;phabet but ina different language.
 Coz

---

### Post by Raeth on 2005-10-08
My tablet works fine now, thought I have a serious problem with The GIMP, which occurs on every distro I try:

I have the stylus enabled and set to screen.
I spawn a new document, and can paint.
The problem is that I can put the brush down, but it does not detect when I pull it up, meaning it thinks the pen is still down.
It is as if it does not detect the "up" signal of the tablet.

The GIMP is the only thing that does this- has anyone an idea what I can do?

Ta, Raeth

---

### Post by djib on 2005-10-13
I just installed Breezy. I have a Wacom Volito 2 and I know it is supported by the wacom linux project (see [http://linuxwacom.sourceforge.net/index.php/main)](http://linuxwacom.sourceforge.net/index.php/main)).
I created a device /dev/wacom0 for my wacom and when I do a xxd /dev/wacom I do get some stuff which means that my tablet is recognised.
Now I can't get the tablet to word !
Here are samples of my /etc/X11/xorg.conf :
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mouse2"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

#Section "InputDevice"
#       Identifier      "Synaptics Touchpad"
#       Driver          "synaptics"
#       Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
#       Option          "Protocol"              "auto-dev"
#       Option          "HorizScrollDelta"      "0"
#EndSection


Section "InputDevice"
        Driver        "wacom"
        Identifier    "stylus"
        Option        "SendCoreEvents"        "true"
        Option        "Device"                "/dev/wacom0"
        Option        "Type"                  "stylus"
        Option        "USB"                   "on"
EndSection

Section "InputDevice"
        Driver        "wacom"
        Identifier    "cursor"
        Option        "SendCoreEvents"        "true"
        Option        "Device"                "/dev/wacom0"
        Option        "Type"                  "cursor"
        Option        "USB"                   "on"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "Synaptics Touchpad"
        InputDevice     "cursor"
        InputDevice     "stylus"
EndSection

```

I don't even get an answer when moving my pen on the tablet.
Any help is welcome !

---

### Post by kxs on 2005-10-19
I had a similar problem with my Intuos tablet. I had to change event number of the tablet in xorg.conf. First it worked with event3, then stoped working at all. I checked again with: sudo xxd /dev/input/event<number>. After that changed the number in xorg.conf to event2 and it works now.

---

### Post by djib on 2005-10-19
Thanks for your answer.
I tried and unfortunately, even when I put event5 (which my tablet, I checked) it still doesn't work.
xxd /dev/input/event5 displays stuff when I move the pen but when I log on X, the pointer doesn't move the mouse...

---

### Post by kxs on 2005-10-19
I don`t know if it helps, but my Intuos works and maybe you want to check my xorg.conf. Maybe you`ll find there something useful.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	# Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
        Option "Type" "cursor"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
        Option "Type" "stylus"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection

Section "InputDevice"
	Driver        "wacom"
	# Intuos3 or Cintiq 21UX
	Identifier    "pad"				 
	# SERIAL ONLY
	#Option        "Device"        "/dev/ttyS0"          
	# USB ONLY
	Option        "Device"        "/dev/input/event2"   
	Option        "Type"          "pad"
	# USB ONLY
	Option        "USB"           "on"                  
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

You don`t have "AlwaysCore" in the Section "ServerLayout" part. Maybe try this.

---

### Post by djib on 2005-10-19
Thanks...
I've been playing around with your xorg file but it still doesn't work...

---

### Post by kxs on 2005-10-19
And what happens when you delete all the tablet lines from the xorg.conf? In my case tablet worked, really poor performance, but worked.
Maybe you should try form the begining, I mean delete the device you`ve created for your Wacom tablet and check what happens.

---

### Post by djib on 2005-10-19
My tablet works fine as a mouse (when there are no lines for it in xorg), but it is not really what I am looking for...

---

### Post by kxs on 2005-10-19
It was the same with my Intuos. Maybe delete the device you created and play only with xorg.conf. I know you tried this, but maybe check again if event5 is the only event that works with your tablet. I had this problem, that event3 seemed OK, but after a while the tablet stopped working and I had to change event to event2 in xorg.conf.

---

### Post by djib on 2005-10-19
Ok, it seems that event2, mouse0 and ts1 are also my tablet. I tried changing it in my xorg file but neither worked. (I did reboot the X everytime)

---

### Post by kxs on 2005-10-20
And do you have these packages installed: wacom-kernel-source, wacom-tools, xserver-xorg-input-wacom? I don`t know if they`re all necessery, but I`ve got them installed.
I`m sorry, but I haven`t got any better idea. It would be great if someone more experienced or just having volito2 tablet checked this subject.

---

### Post by djib on 2005-10-20
Hey,
I tried installing those packages and it doesn't work either.
Thanks a lot for your help...
Hope a Wacom Volito2 user drops by come day...

---

### Post by cosimo on 2005-12-05
OK Forget everything I have posted pryor to this because I am an idiot!!!
 I build and repair computers for a living right now, so i do alot of testing. Last week I uninstalled ubuntu, and installed Kubuntu, to try it again. Well I don't like Kubuntu so i uninstalled that and reinstalled ubuntu again. 
   I did what I ususally do for the wacom tablet , graphire2, and i am getting the same problems, however, NONE of what I did before to stop things like the scroll wheel jitter, or Gimp not releasing the tools, has helped!!!
 SO, Below is my xorg.conf, if ANYONE has different settings and their tablet works in gimp and the scroll wheel doesn't jitter, i would appreciate it if you post the relevant part of your xorg!!


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"True"
	Option		"ZAxisMapping"		"4 5"
EndSection


Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "cursor"
        Option "USB" "on"
        
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "stylus"
        Option "USB" "on"
        Option "ZAxisMapping"                            "4 5"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection




Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection

---

### Post by cristophine on 2005-12-06
Hi,

I have a e3works stylo and I'm trying to get it setup using the wacom driver. I cant seem to find the tablet in /dev/input/. The keyboard is on event0 and the mouse on event1. There is an event2 as well but I cant seem to find where it goes to.

Instead, I've found the tablet on /dev/usb/hiddev0. However, when I put this in the device field in xorg.conf I get this on X startup (from the log):

(**) Option "Device" "/dev/usb/hiddev0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument
(**) Option "Device" "/dev/usb/hiddev0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument
(**) Option "Device" "/dev/usb/hiddev0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument

My guess is incompatible drivers. I do have the windows drivers if that helps. Any ideas?

---

### Post by cristophine on 2005-12-07
I tried using the mouse driver and the device loads in x properly (no errors); the tablet registers as a 5 button mouse I think. The only problem is configuring it to run properly...

---

### Post by commodore on 2005-12-11
When I use my wacom in GIMP it goes very wierd. I cannot use my wacom on the interface- I can't press buttons or anything. After using wacom my mouse wont work either. Ctrl+Q doesn't help either so the only way out I know is Ctrl+Alt+backspace :D:D

What's wrong? I have Wacom Volito.

---

### Post by djib on 2005-12-11
[QUOTE=commodore]When I use my wacom in GIMP it goes very wierd. I cannot use my wacom on the interface- I can't press buttons or anything. After using wacom my mouse wont work either. Ctrl+Q doesn't help either so the only way out I know is Ctrl+Alt+backspace :D:D

What's wrong? I have Wacom Volito.[/QUOTE]

If you have a Volito 2, it is not compatible with breezy. I guess it will be in dapper (I'm using dapper and I got better results though not excellent yet)...

---

### Post by commodore on 2005-12-13
I have Volito 1.

---

### Post by djib on 2005-12-13
I don't know then, sorry.

---

### Post by MetalMusicAddict on 2006-01-12
[QUOTE=commodore]When I use my wacom in GIMP it goes very wierd. I cannot use my wacom on the interface- I can't press buttons or anything. After using wacom my mouse wont work either. Ctrl+Q doesn't help either so the only way out I know is Ctrl+Alt+backspace :D:D

What's wrong? I have Wacom Volito.[/QUOTE]
Im getting the same here with my Wacom. Im looking into it. **<- EDIT. I figured it out and will update tomorrow.** :)

Also, Ill be updating the 1st post soon to try to cover the issues that have appeared in the thread.

---

### Post by MetalMusicAddict on 2006-01-14
Updated.

commodore, The update should fix your problems.

---

### Post by djib on 2006-01-14
Hello,
Thanks for updating the post.

In the very first stage, when I plugged in my tablet and typed ```
dmesg | grep wacom
``` I got no answer.
Typing ```
dmesg | tail
``` gave me the following.
```
[4295252.840000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[4295253.034000] input,hiddev96: USB HID v1.10 Mouse [WACOM CTF-420 V2.0-0] on usb-0000:00:1d.1-2

```
I have not gone any further since it was not the expected result. What do you think?

---

### Post by MetalMusicAddict on 2006-01-14
Sorry djib. I messed up. I ment to post commodores issue should be fixed.

But... I did notice that the xorg you posted your input sections look like this:
```
Section "InputDevice"
        Driver        "wacom"
        Identifier    "stylus"
        Option        "SendCoreEvents"        "true"
        Option        "Device"                "/dev/wacom0"
        Option        "Type"                  "stylus"
        Option        "USB"                   "on"
EndSection
```
When it should look like:
```
Section "InputDevice"
        Driver        "wacom"
        Identifier    "stylus"
        Option        "SendCoreEvents"        "true"
        Option        "Device"                "/dev/**input**/**event**0"
        Option        "Type"                  "stylus"
        Option        "USB"                   "on"
EndSection
```
The 3 parts of the pad should be mapped to a event.


Heres another way to detect the driver. Turn on PC with the pad in first.
In a terminal: (open your terminal nice and long)
```
**more /proc/bus/usb/devices**
```

You should get a section something like this:
```
T:  Bus=04 Lev=03 Prnt=05 Port=00 Cnt=01 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056a ProdID=0011 Rev= 2.03
S:  Manufacturer=WACOM
S:  Product=ET-0405A-UV2.0-3
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 40mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=wacom
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```


[HERES]("http://linuxwacom.sourceforge.net/index.php/howto/testtablet") is where this info came from and might be clearer.

---

### Post by izm81 on 2006-01-15
Hi all.  I've always had trouble getting my wacom graphire (I) to work on Breezy and now Dapper.  I've tried all the steps in the root post (and read all the others), but when I go to configure Gimp, it says I have no extended input devices.

I can get readings from wacdump.  I can use the stylus without pressure, and with a few extra problems.  The mouse is still in absolute mode, even though I have the "relative" option in my xorg.conf.

my xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "cursor"
	Option        "Mode"          "relative"
	Option        "USB"           "on"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "stylus"
	Option        "USB"           "on"
	Option        "PressCurve"    "0,0,100,100"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "eraser"
	Option        "USB"           "on"
EndSection

Section "Device"
	Identifier	"TI4200"
	VendorName	"nvidia"
	Driver		"nvidia"
#	Driver		"vesa"
#	Driver		"nv"

	BusID		"PCI:01:00:0"
#	VideoRam	131072
	Option		"UseFBDev"		"true"

#	glxgears -iacknowledgethatthistoolisnotabenchmark
#	NOTE: NvAgp NOT optional, for me....
	Option		"NvAgp"			"0" # works 2700 fps
#	Option		"NvAgp"			"1" # works 2800, then 3300
#	Option		"NvAgp"			"2" # doesn't work
#	Option		"NvAgp"			"3" # doesn't work

#	RenderAccel is experimental, be safe
#	Option		"RenderAccel"		"true"

#	Option		"sisAGP"		"1" # works?
EndSection

Section "Monitor"
	Identifier	"Compaq v70"
	Option		"DPMS"
	#HorizSync	30-70
#	VertRefresh	50-160
	VertRefresh	40-60
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"TI4200"
	Monitor		"Compaq v70"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"cursor"		"SendCoreEvents"
	InputDevice	"stylus"		"SendCoreEvents"
	InputDevice	"eraser"		"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

any ideas?  Thanks.


screen of wacdump attached:

---

### Post by MetalMusicAddict on 2006-01-15
Your problem is kinda like the post above yours. The **device** needs to be mapped to an **event**. Shouldnt say **wacom**. I would suggest starting at the beginning from the 1st post. My updated instructions.

---

### Post by izm81 on 2006-01-15
Thanks for the reply.

/dev/input/wacom just links to the event that is created for the tablet.  I've tried both the correct event and the wacom link, with the same results.

I did find something strange...  If I look at /var/log/Xorg.0.log, I see this:
```

(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
[B](EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'[/B]
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Sun Jan 15 16:30:11 2006: 16470 X: client 2 rejected from local host
AUDIT: Sun Jan 15 16:30:11 2006: 16470 X: client 4 rejected from local host
AUDIT: Sun Jan 15 16:30:11 2006: 16470 X: client 3 rejected from local host
AUDIT: Sun Jan 15 16:30:11 2006: 16470 X: client 5 rejected from local host

```

But when I look at dmesg, it looks like the driver is registering:
```

[4295444.043000] usbcore: deregistering driver wacom
[4295482.098000] input: Wacom Graphire as /class/input/input4
[4295482.138000] usbcore: registered new driver wacom
[4295482.138000] drivers/usb/input/wacom.c: v1.44:USB Wacom Graphire and Wacom Intuos tablet driver

```

Any ideas?  Thanks!

---

### Post by MetalMusicAddict on 2006-01-15
Did you do step **2** from the guide? What do you get?

---

### Post by izm81 on 2006-01-15
```

steve@semper:/dev/input $ ls -l
total 0
crw-rw---- 1 root root 13,  64 2006-01-15 02:00 event0
crw-rw---- 1 root root 13,  65 2006-01-15 02:00 event1
crw-rw---- 1 root root 13,  66 2006-01-15 16:34 event2
crw-rw---- 1 root root 13,  67 2006-01-15 02:00 event3
crw-rw---- 1 root root 13,  63 2006-01-15 02:00 mice
crw-rw---- 1 root root 13,  32 2006-01-15 16:34 mouse0
crw-rw---- 1 root root 13,  33 2006-01-15 02:00 mouse1
crw-rw---- 1 root root 10, 223 2006-01-15 02:02 uinput
lrwxrwxrwx 1 root root       6 2006-01-15 16:34 wacom -> event2

```

At first, it was event3, then the next time i booted it was event2.  Either way, wacom seems to point to the correct device.  "cat"ing the output from either of those devices (wacom or effective event#) gives a bunch of gibberish when moving the stylus, like it says in the guide.

---

### Post by sutech on 2006-01-18
Hi.
Thanks to this HOWTO my Wacom Volito 1 is functional... but i have one problem. I'm using twinview (i have 2 monitors) and I have shifted cursor in GIMP. Well the drawing cursor is shifted aprox. 30px to left and 30px up on Screen 1 (17" monitor, 1280x1024) and apox. 1280px to left and 30px up on Screen 2 (19" monitor, 1280x1024). I want to work on the bigger screen, but it's impossible. This shift occurs only when I enable stylus, eraser and cursor in GIMP. When they are disabled, everything works normaly, but I don't have pressure sensitivity. Please help me

Here is my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/event2"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"PressCurve"	"50,0,100,50"
	Option		"TwinView"	"horizontal"
	#Option		"ScreenNo"	"1"
	#Option		"KeepShape"	"on"
	#Option		"TopX"		"0"
	#Option		"TopY"		"0"
	#Option		"BottomX"	"1280"
	#Option		"BottomY"	"1024"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/event2"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
	Option		"PressCurve"	"50,0,100,50"
	Option		"TwinView"	"horizontal"
	#Option		"ScreenNo"	"1"
	#Option		"KeepShape"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/event2"
	Option		"Type"		"cursor"
	Option		"USB"		"on"
	Option		"PressCurve"	"50,0,100,50"
	Option		"TwinView"	"horizontal"
	#Option		"ScreenNo"	"1"
	#Option		"KeepShape"	"on"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"IBM L171"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"IBM L171"
	Option		"TwinView"		"On"
	Option		"TwinViewOrientation"	"RightOf"
	Option		"MetaModes" "1280x1024,1280x1024;1024x768,1024x768;1280x1024,NULL;1024x768,NULL"
	Option		"SecondMonitorHorizSync"	"31-81"
	Option		"SecondMonitorVertRefresh"	"50-76"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by fp-www.tonepad.com on 2006-01-21
I haven't had any success trying to get my GRAPHIRE4 working besides it behaving just  like a mouse.

---

### Post by firekat on 2006-01-27
Thanks!!!

I did finally get my Graphire Pad working.  Have not tried it on Gimp as I am addressing lots of other installation/setup issues.

I was about to pack it in totally on Ubuntu as it was 3+ strikes (mouse, sound, video, grub).  I just can't spend so much time trying to get it to work right!  

It was most irritating that the mouse would not behave properly.  The scroll wheel was backwards!  Try that!  My serial mouse would not work - though the scroll wheel did - in the right direction.  Now both work, though I would like it if the Graphire mouse would move quicker with less movement to get it across the screen.  At least it is working in "relative" mode versus "absolute" which is a big pain for mouse movement.  Also the Graphire does not seem to "jitter" like it did before.

Thanks Again!

---

### Post by lcampagn on 2006-01-27
I had to manually run "modprobe evdev" before my event devices were created. I hope this helps anybody else with similar problems..

---

### Post by nacs on 2006-02-15
Thanks for the howto.

Got my intuos3 today, Googled 'ubuntu intuos3', came here and got it all setup and working on first try. :mrgreen: 

The only small 'problem' I had was that GIMP was treating the tablet input like a normal mouse (with no regard for pressure and such).

Then I figured out that you have to do the following to get it all working in GIMP:
[LIST=1]
[*]Goto "File" then "Preferences"
[*]Select "Input Devices"
[*]Click "Configure Extended Input Devices"
[*]In the new dialog, select each drop down item "cursor", "eraser", "stylus", etc and set "Mode" to "Screen" (from "Disabled")
[/LIST]

I initially set "Mode" in the last step to "Window" but that made the GIMP cursor un-aligned with the KDE / X cursor so I set it to screen which made it work correctly.

---

### Post by MetalMusicAddict on 2006-02-15
> **nacs]Thanks for the howto.

Got my intuos3 today, Googled 'ubuntu intuos3', came here and got it all setup and working on first try. :mrgreen: 

The only small 'problem' I had was that GIMP was treating the tablet input like a normal mouse (with no regard for pressure and such).

Then I figured out that you have to do the following to get it all working in GIMP:
[LIST=1]
[*]Goto "File" then "Preferences"
[*]Select "Input Devices"
[*]Click "Configure Extended Input Devices"
[*]In the new dialog, select each drop down item "cursor", "eraser", "stylus", etc and set "Mode" to "Screen" (from "Disabled")
[/LIST]

I initially set "Mode" in the last step to "Window" but that made the GIMP cursor un-aligned with the KDE / X cursor so I set it to screen which made it work correctly.[/QUOTE]
Yep. Already #7 in the guide.  said:**
> **7.** Enable the tablet in The GIMP.
- **File**-> **Preferences**-> **Input Devices**-> "Configure Extended Input Devices".
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".

---

### Post by nacs on 2006-02-15
Wow. Not sure how I missed that. :eek:  :-\"

---

### Post by Cesium on 2006-02-22
Thanks for the HowTo.  I am fairly new to Linux and understand the HowTo up until step 3.  How do I "Add this below Section "InputDevice" under the "Configured Mouse". Make sure you use the right "Device" based on how your pad is connected. ie: USB or serial"?

Thanks.

---

### Post by FlakJacket on 2006-02-24
Excellent tutorial worked without a hitch.  Cesium (like the name btw) you need to edit your /etc/X11/xorg.conf file with the changes he suggests. use

```
 sudo nano /etc/x11/xorg.conf
```

I was grateful to find that I didn't have to change mouse names as I had already done so when I configured my Logitech G5.

Thanks alot,
Flak

---

### Post by FlakJacket on 2006-02-28
For some reason my tablet keeps changing event #'s any idea why?

Thanks,
 Flak

---

### Post by robinl on 2006-03-10
Great tut and thank you now my intuos 3 is working fine. However, I want to ask a question: can I map the tabs on the side of the drawing area of my intuos 3 to something else like I want to assign left strip to scrolling up or down but I cannot find a way to do it.

---

### Post by MetalMusicAddict on 2006-03-10
Good question. Im not sure but give a look to the two links at the top of the 1st post. They might be of help. I didnt see any mention of your specific tablet though. Google around. [img]http://ubuntuforums.org/images/lite/icons/icon13.gif[/img]

---

### Post by robinl on 2006-03-13
No luck. Can't seemed to find anything for side buttons. Does Graphire 4 have the same problem? Keyboard shortcut doesn't recognise it Is there any way I can remap things? I'm really not used to middle button being the lower button on the stylus and maybe i could use the same method to map the buttons on the sides of my tablet.

---

### Post by Mikebgr on 2006-03-25
Hey metalhead :) Great job. My tablet works now (wacom graphire 3), but I still have problems! 1st is with wheel, i cannot scroll either up or down (it looks as if it scrolls a bit down, and a bit up, and its one and the same, like:  -5 lines, + 5 lines = 0 lines).

My guess this happens because in ubuntu there is "reverse" scrolling, eg: when you scroll the mouse wheel towards you the side bar goes up instead of down, but I dont know how to fix that! (newb :( )

Second is with my cursor being absolute, when i have set it to relative through   ```
Option        "Mode"          "relative"
```

Maybe the bundled wacom drivers dont have a "mode" option? I haven't tried installing the drivers from linuxwacom as i'm not sure what will happen and if i will be able to reverse it.

One final note, i tried setting 

```
	Option		"Emulate3Buttons"	"true"
```

to false, but it doesnt seem to make any difference. Anyone knows what that does?

Here is my xorg.conf btw

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event1"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event1"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event1"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41 [GeForce 6800?]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41 [GeForce 6800?]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "stylus"    "SendCoreEvents"
        InputDevice     "eraser"    "SendCoreEvents"
        InputDevice     "cursor"    "SendCoreEvents"    #For non-LCD tablets only
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

---

### Post by MetalMusicAddict on 2006-03-25
Your talkin about your Wacom mouse right? Ill look into it but I think it'll act just like your normal mouse. Dont know if you can seperate the two. Ill look. Look through the two links at the top of the first post also.

---

### Post by Mikebgr on 2006-03-25
both problems [COLOR="Blue"]solved[/COLOR]!


Solution: It seems like primary pointer status must be set for "cursor" via

```
$: sudo xsetpointer cursor
```

Yay! I dont know if that will create any trouble with gimp. I am downloading it right now, so if any trouble occurs I will update ;)

By the way I wonder if its really neccessary to have Mouse0/mice as a pointing device altogether. I will also test on that and update!

Update: Commenting out mouse0 (normal mouse) in xorg.conf crashes my x at startup, some weird dependency i suppose with HAL.  No problems with gimp and cursor set as corepointer either!

---

### Post by Mortimer on 2006-03-27
Would anyone know how to set the screen mappings. I don't mean the button mappings, though that would be nice too. But I mean setting the active area to a part of the screen instead of all of it. This helps older tablets with mismatched aspect ratio related to a standard screen. 

Hoping someone knows or cares about what I'm talking about. If it's not possible here, oh well that's fine. Would be nice to know that if it's the case.

---

### Post by Mikebgr on 2006-03-28
There must be an "option" command for it, in stylus and eraser inputdevice sections, but I'm not familiar with those options (like PressCurve, I found out about it here). Anyone knows where to get a full list of the driver's options?

---

### Post by StkvDba on 2006-03-31
[QUOTE=Mikebgr]There must be an "option" command for it, in stylus and eraser inputdevice sections, but I'm not familiar with those options (like PressCurve, I found out about it here). Anyone knows where to get a full list of the driver's options?[/QUOTE]

Check out the [Linux Wacom Project HOWTO Section 5.1, "Adding the InputDevices"]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev") for a listing of the driver's options.

The Options I believe Mortimer is interested in are:

```
Option "TopX" "number"
                   X coordinate of the top corner of the active zone.

Option "TopY" "number"
                   Y coordinate of the top corner of the active zone.

Option "BottomX" "number"
                   X coordinate of the bottom corner of the active zone.

Option "BottomY" "number"
                   Y coordinate of the bottom corner of the active zone.
```

These forums have been invaluable in helping me get my Graphire4 working beautifully - thanks!

---

### Post by MetalMusicAddict on 2006-03-31
Ahh... Nice StkvDba. :) Where did you see this? Wacom page?

---

### Post by StkvDba on 2006-03-31
[QUOTE=MetalMusicAddict]Ahh... Nice StkvDba. :) Where did you see this? Wacom page?[/QUOTE]

Yep, it's Section 5.1 of the Linux Wacom Project HOWTO.  When you click the link I reference, scroll down a bit and you'll find the updated man page for the wacom driver, listing all the options, with descriptions of what they do.  To summarize them:

```
        Option "Type" "stylus"|"eraser"|"cursor"|"pad"
        Option "Device" "path"
        Option "USB" "on"
        Option "ForceDevice" "ISDV4"
        Option "DeviceName" "name"
        Option "Suppress" "number"
        Option "Mode" "Relative"|"Absolute"
        Option "TopX" "number"
        Option "TopY" "number"
        Option "BottomX" "number"
        Option "BottomY" "number"
        Option "ButtonsOnly" "on"
        Option "ButtonM" "N"
        Option "TPCButton" "on"
        Option "Speed" "Rspeed"
        Option "Twinview" "horizontal"|"vertical"|"none"
        Option "TVResolution" "res1,res2"
        Option "ScreenNo" "n"
        Option "Rotate" "CW"|"CCW"|"NONE"
        Option "PressCurve" "x1,y1,x2,y2"
        Option "KeepShape" "on"
        Option "DebugLevel" "number"
        Option "Serial" "number"
        Option "Threshold" "number"
```

I've got to give you much credit, MetalMusicAddict!  Couldna done it without you!

---

### Post by MetalMusicAddict on 2006-03-31
Thanx man. :) I just put it together a little easier to read. The Wacom page has all this info like you said but it gets confusing sometimes.

---

### Post by FlakJacket on 2006-03-31
Does anyone know why my Wacom Graphire3's /dev/input/event# keeps changing every time I restart?  Any guidance is appreciated.

Thanks,
Flak

---

### Post by StkvDba on 2006-03-31
[QUOTE=FlakJacket]Does anyone know why my Wacom Graphire3's /dev/input/event# keeps changing every time I restart?  Any guidance is appreciated.

Thanks,
Flak[/QUOTE]

Yeah, I had the problem with event numbers changing, too.  I have a USB mouse in addition to the USB Wacom tablet.  I tried /dev/input/wacom instead, and haven't had any problems.

(Of course, I also compiled my own kernel with the new wacom.c and hid-core.c and used the prebuilt wacom_drv.o - so who knows what combination of these conspired toward my success.)

---

### Post by StkvDba on 2006-03-31
[QUOTE=StkvDba]Yeah, I had the problem with event numbers changing, too....[/QUOTE]

Just thought of something else... you might check your **/etc/udev/rules.d/10-wacom.rules** to make sure the following line is there:

```
KERNEL="event*", SYSFS{idVendor}="056a", NAME="input/%k", SYMLINK="input/wacom%e" 
```

This came from Olivier Lecarme's [Installing a Wacom tablet on a Debian Distribution]("http://www.i3s.unice.fr/~ol/success.html").

Hope that helps!

---

### Post by MetalMusicAddict on 2006-03-31
Let us know how StkvDba's advice works.

---

### Post by FlakJacket on 2006-04-01
I don't have a file named 10-wacom.rules . Should I make one and put that in there?

Thanks,
Flak

BTW I have a USB mouse also.

---

### Post by StkvDba on 2006-04-01
[QUOTE=FlakJacket]I don't have a file named 10-wacom.rules . Should I make one and put that in there?[/QUOTE]

I believe that script comes with the package wacom-tools.  Try

```
sudo apt-get install wacom-tools
```

and see if it shows up.

I pretty much followed the Linux Wacom Project's HOWTO and MetalMusicAddict's suggestions step-by-step to get mine working, but I don't recall who told me to install that package...

---

### Post by Mortimer on 2006-04-05
> The Options I believe Mortimer is interested in are:

Incorrect, those are to change the tablet active area. I contected the driver author and he said that other feature is not supported yet. -_- I did use it in windows, so I will miss it.

---

### Post by PowerLlama on 2006-04-07
[QUOTE=StkvDba]I believe that script comes with the package wacom-tools.  Try

```
sudo apt-get install wacom-tools
```

and see if it shows up.

I pretty much followed the Linux Wacom Project's HOWTO and MetalMusicAddict's suggestions step-by-step to get mine working, but I don't recall who told me to install that package...[/QUOTE]
I think this should be added to the first post, because mine wasn't working until I did this. I could tap on the tablet and get it to register clicks, but I couldn't get the pointer to move.

Now the pointer is moving, but I don't seem to have pressure-sensitivity in the gimp.

Edit**   Nevermind, I fixed the sensitivity.

---

### Post by FlakJacket on 2006-04-12
wacom-tools worked! Now it's dev/input/wacom and it doesn't change!

Thanks a bunch,
Flak

---

### Post by MetalMusicAddict on 2006-04-12
Justa FYI.

Im trying to get this to work on Dapper but Im hitting snags. I hope having XGL running doesnt have something to do with it. :(

---

### Post by FlakJacket on 2006-04-12
Has anyone used Pixel? I says it doesn't support wintab. Any idea if that just means SOL?

Thanks,
Flak

---

### Post by indigoshift on 2006-04-15
Thanks for the information!  My Intuos3 is working great on my Thinkpad G40.  Mouse and stylus both.  As a (semi-retired) commercial illustrator, I'm tickled pink that there's one less thing I need my Windows machine for.

Oddly, nothing in this thread worked at all until I did the "sudo xsetpointer cursor" trick that Mikebgr suggested, which immediately froze my mouse.  Mikebgr, I'm sorry I said those things about you under my breath before I hit ctrl+alt+backspace.  :mrgreen: 

After that, it worked great.  :D 

MetalMusicAddict, would you mind if I rewrote your first post into an easy to follow, step-by-step procedure?  The information is great, just a little hard to follow.  Well, for me, at least.

---

### Post by HunterPro on 2006-04-15
Indigoshift: I had the same feeling :)

I've been doing 'that Ubuntu thing' for some time now (guess around 5 months, had Debian testing on my laptop before that, but ubuntu is just way better for desktopstuff), and since a few weeks I'm on Dapper Drake. No XGL btw - still wanna try that but didnt have the time for it.

Could use everything on my laptop - except my Intuos3 A5. And since I'm studying Industrial Design, I kinda need the thing. Now i'm completely Windows-free - wow!

btw, the tips in the startpost were magical. It didnt work at first - until I saw some familiar lines in de Xorg.0.log:

(EE) No Input driver matching `synaptics'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'

and then I remembered that I had a similar problem with my touchpad - so I went for the apt-cache search wacom - and there it was: xserver-xorg-input-wacom :) :) after apt-getting that one (and also the synaptics driver for my touchpad - somehow I lost it during the upgrade to Dapper) and restarting X, my Intuos3 works fine! It actually doesnt have some annoying feats that the windows driver does have.

Thanks Ubuntu for releasing me from Windows! :P

offtopic: I don't know if this forum supports it, but shouldnt this topic be moved to a breezy or dapper subforum, or at least have something like aliases, clone-topics or whatever they're called here in those subforums? :)

---

### Post by MetalMusicAddict on 2006-04-15
[QUOTE=HunterPro]offtopic: I don't know if this forum supports it, but shouldnt this topic be moved to a breezy or dapper subforum, or at least have something like aliases, clone-topics or whatever they're called here in those subforums? :)[/QUOTE]
Im not sure what you mean?

If you mean a Wacom-Breezy and a seperate Dapper one I plan on maintaining this thread for both.

Im working out the Dapper HOWTO now. I got some bugs. They might be XGL related.

So no matter Breezy or Dapper Im gonna keep this topic up-to-date. :)

---

### Post by HunterPro on 2006-04-15
[QUOTE=MetalMusicAddict]Im not sure what you mean?

If you mean a Wacom-Breezy and a seperate Dapper one I plan on maintaining this thread for both.

Im working out the Dapper HOWTO now. I got some bugs. They might be XGL related.

So no matter Breezy or Dapper Im gonna keep this topic up-to-date. :)[/QUOTE]
thats great :D its just that with stuff like (ugh) phpbb you can have shortcuts to topics from subforum a to b, so you can like uhm place a shortcut in the breezy forum to this topic. Cause the only way people are going to find this topic is through the search function, not by logical browsing, since its in the hoary part of the forums. :) So I kinda wondered if this forum software also supports that sort of stuff (I guess you'll need a moderator for that anyway :))

btw, major thanks for maintaining this topic! :)

---

### Post by HanZo on 2006-06-03
still looks like XGL and wacom don't go along too well... had anyone any success in solving this problem? I do most of my work with the tablet (I'm an illustrator) so for now I had to get back to plain X... but having XGL would be really nice... 
How was that thing with the workaround? sorry I'm not the total noob, but I still need to learn some things... how can I have 2 different sessions with different window managers running in parallel?
thanks in advance for any help!

---

### Post by MetalMusicAddict on 2006-06-03
HunterPro. Im gonna get this put in the Dapper Tips and Tricks. Maybe we should have a general one? Tips and Tricks section that is.

[QUOTE=HanZo]still looks like XGL and wacom don't go along too well... had anyone any success in solving this problem? I do most of my work with the tablet (I'm an illustrator) so for now I had to get back to plain X... but having XGL would be really nice... 
How was that thing with the workaround? sorry I'm not the total noob, but I still need to learn some things... **how can I have 2 different sessions with different window managers running in parallel?**
thanks in advance for any help![/QUOTE]
I havnt had a chance to re-install XGL/Compiz yet. I did a clean Dapper-Final reinstall and its running like a dream. Kinda dont wanna mess it up. :( 

I thought there was a way to run 2 xsessions at the same time. I think this is how people are running GL games without problems. Give a look over at the Compiz forums.

---

### Post by Loïc2 on 2006-06-03
[QUOTE=MetalMusicAddict]
If anyone has info to make this better let me know. ;)[/QUOTE]
 Hi,
I've created a quick guide for Ubuntu Dapper, easier and more up to date 
than the previous one on the wiki.

It's at [https://wiki.ubuntu.com//Wacom](https://wiki.ubuntu.com//Wacom)

It also has screen captures and even though it doesn't detail everything, it's done to keep it as simple as possible.

If you want, you can edit your first post to add it among the links :) and edit the wiki (or write me an email) for sections you think could be improved.

Thanks

---

### Post by MetalMusicAddict on 2006-06-03
Nice. Ill look through it. It does seem to have become much more simple. Ill try the WIKI way on my laptop and test it with XGL/Compiz and get back to you. ;)

---

### Post by PowerLlama on 2006-06-04
I just wanted to say, I tried the wiki, and couldn't get it to work properly. Instaed of controlling the whole screen, my tablet would only control a small portion of it. Did it like it says in the beginning of this thread and it works fine.

---

### Post by HanZo on 2006-06-04
> Instaed of controlling the whole screen, my tablet would only control a small portion of it
It did the same for me before editing the xorg.conf. so maybe you just made some error there. One thing I did not see the fist time I followed the howto was that you have to delete or comment some lines... otherwise you'll have options for both usb and parallel and that messes up the driver (or X or whatever does the stuff).
Btw. the howto is great! it was just me who was too lazy to read everything...
> Give a look over at the Compiz forums
I'll do it... again... it's always a mess to find the info you're looking for here... there's just sooooo much stuff in here (which anyway is a good sign IMHO).

---

### Post by MetalMusicAddict on 2006-06-04
[QUOTE=PowerLlama]**I just wanted to say, I tried the wiki, and couldn't get it to work properly.** Instaed of controlling the whole screen, my tablet would only control a small portion of it. Did it like it says in the beginning of this thread and it works fine.[/QUOTE]
Im sure Loïc2 would like some feedback on what didnt work for you.

---

### Post by PowerLlama on 2006-06-06
Bah, I just did it again and found out what I did wrong with the wiki.

I did exactly what hanzo did and didn't comment out stuff. You should add that to the wiki so that no one else gets confused.

---

### Post by TuxCrafter on 2006-06-08
Hello,

I have got my Wacom Graphire 3 working beautifully under ubuntu and fedora, thank you all.

I have a guestion: what is the function of the cursor device?

If i use the wacom mouse gimp goes to the cursor device but can´t do anything.

If i disable the cursor in the gimp, then the wacom mouse is going to the core cursor and everything works as a normal mouse.

So what is the wacom cursor device?

Also i use synergy to share 1 mouse/wacom device and one keyboard for two pc. beautiful program. But it doesn't work with the styler pen. I believe synergy can´t handle absolute value's. I had the same behavior under running synergy in a Vmware machine.

Also i seek a function/tool that i can use the wacom device to enter text. Like the pen of a pda. Some sort of program  that i can start that detects moves and translate it to characters. End a easy way of activation en disabling this function.

Is there a solutions for these problems/features?

---

### Post by TuxCrafter on 2006-06-08
please look at my previus post!!

Here i am again with some tips:

cd /dev/input/
ls
sudo cat wacom

replace in xorg.conf
Option        "Device"        "/dev/input/event0"
to
Option        "Device"        "/dev/input/wacom"

I don't have my wacom graphire 3 connected always. I saw my X crashing because it was getting things from a event input that wasn't my wacom device.

I believe using wacom in xorg is saver 8-)

btw does somebody now a bash script that closes X and restart it automatic without asking me for info. This would be very nice for my TV <-> CRT scripts.:-k

---

### Post by flaimo on 2006-06-26
can somebody help me with setting up the two buttons on the pen? in windows the upper one is assigned to a doubleclick and the lower one is the right click. after installing the tablet in linux however the upper button is the right click and the lower one isn't workling at all. i would like the same behaviour as in windows.

at [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev) there is note about Option "ButtonM" "N". but i don't know which number each button has and what the "N" codes are for double click and right click.

---

### Post by flaimo on 2006-06-27
bump.

can't believe that nobody has changed their buttons on the pen &#8230;

---

### Post by TuxCrafter on 2006-06-27
I would like to now it how it is possible two,

I used the wacom under windows and than i can hold the "middle mouse" button and can scroll a webpage.

Under linux the middle mouse button is "copy/past" so scrolling doesn't work i would like to see if i can change this.

---

### Post by Ertain on 2006-06-27
Hello everyone.  First time posting!

I've followed nearly all of the stuff necessary to make my Graphire 4 work.  But it still doesn't work properly. ](*,)  Even when I hold the tip of the stylus a centimeter above the drawing surface it registers it as a button press.  I'm using drivers version 0.7.4.  The sensitivity does work, but when I lift off the stylus while still keeping in proximity it still seems to draw.

**_Update_**
After going through the arduous task of getting my tablet to work, I have finally solved the problem.  Apparently my computer kept thinking it was a mouse.  So I made it so that my tablet is found first by editing /etc/modules to load the wacom module first.  And since wacom-tools can't seem to find my tablet through it's normal means, I've had to edit my /etc/X11/xorg.conf file to use the /dev/input/event3 devices.  I've also taken the liberty of making the wacom rules for udev load first (by making them 10-wacom.rules instead of maybe 45-wacom.rules in the /etc/udev/rules.d directory).

---

### Post by prokoudine on 2006-07-14
Followed this tutorial and neither Inkscape, nor GIMP or Krita recognize my wacom devices on Dapper Flight. Stylus itself works as usual mouse device.

Here is excerpt from my xorg.cong:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"	"CoreKeyboard"
	InputDevice    "Configured Mouse"	"CorePointer"
	InputDevice    "Synaptics Touchpad"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mouse0"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/input/event4"   # USB ONLY
	Option        "Type"          "stylus"
	Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/input/event4"   # USB ONLY
	Option        "Type"          "eraser"
	Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/input/event4"   # USB ONLY
#	Option        "Device"        "/dev/input/wacom"   # USB ONLY
	Option        "Type"          "cursor"
	Option        "USB"           "on"                  # USB ONLY
EndSection

```

---

### Post by km0ti0n on 2006-07-16
Thanks for the how to.

It's works, as you'd expect, on Dapper.  There's one thing I found when trying to discover what event# the table is on was to just use wacdump.  

```
sudo wacdump /dev/input/event#
```

When using that it obovoius which device to set the xorg.conf file to.

km0ti0n

---

### Post by graigsmith on 2006-07-16
prokoudine, you don't need to determine what event the device is on, let wacom-tools do the work of finding and creating a link to your tablet.

install the package wacom-tools

change the device from event4 to /dev/input/wacom

also remove comments at the end of the wacom device lines.  that messes things up, if anything move them to the next line. or just delete them.

when you are finished your wacom section in your xorg.conf file should look like this. if it is a usb tablet.

```

#Wacom Section

Section "InputDevice"
	Identifier "cursor"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "cursor"
	Option "USB" "on"
	Option "Mode" "Relative"
EndSection

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "USB" "on"
	Option "PressCurve" "50,0,100,50"
	Option "Mode" "Absolute"
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "eraser"
	Option "USB" "on"
	Option "Mode" "Absolute"
EndSection

```

dont forget to add the last 3 things to your server layout section.
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice "cursor" "AlwaysCore"
	InputDevice "stylus" "AlwaysCore"
	InputDevice "eraser" "AlwaysCore"
EndSection

``` 
after that reboot and it should work.

---

### Post by TuxCrafter on 2006-07-26
Hello

I have a problem with my wacom tablet under xubuntu.

When I dubble click with a normal mouse on the title bar of a window it will toggle between normal and maximize windows size. When i want to do this with my wacom stylus it will not work.

I figured out why it will not work can it be fixed?

>
The window manager want the dubble click at the exact same spot. And this is no problem with a normal mouse because it stands still. But with a handhold stylus this is almost imposable and very trick to accomplish. Even with mouse settings the most insensitive settings.

>
I also have the problem that there is no scrollweel on the stylus. And I can't scroll. How do I change settings that a mouse button click will automatic grab the scrollbar when it is pressed. Then I can just move the pointer and the the scrollbar will move too.

I also posted this question on the xubuntu dev list.

Please help me?

---

### Post by prokoudine on 2006-07-29
**graigsmith**

Thank you, but that doesn't help :(

---

### Post by TuxCrafter on 2006-07-29
> **prokoudine said:**
> **graigsmith**

Thank you, but that doesn't help :(

start the gimp 
>
file->preferences->input devices
>
config extended input devices
>device = stylus
>mode = screen

same thing for the eraser

restart the gimp end post result.

---

### Post by prokoudine on 2006-07-31
**TuxCrafter**

I do know what to do in GIMP :) It's just doesn't list stylus/eraser/cursor in the combobox, only synaptics touchpad - that's what I'm talking about :)

---

### Post by TuxCrafter on 2006-07-31
> **prokoudine said:**
> **TuxCrafter**

I do know what to do in GIMP :) It's just doesn't list stylus/eraser/cursor in the combobox, only synaptics touchpad - that's what I'm talking about :)

ow sorry, i just wanted to help. maybe you can reconfigure your xserver and try to do setup your wacom tablet again maybe it will work then. be sure to backup your xorg file bevore executing the reconfig.

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
dpkg-reconfigure xserver-xorg
```

---

### Post by hirumono on 2006-08-04
Hi to everybody, my first post here and I wanted to thank all of you for helping me make my Wacom Graphire 2 work in Ubuntu Breezy. It took almost 3 days, but at the end, man won over machine... ;) Thanks in particular to MetalMusicAddict and Loïc2 for their well-made guides.
I also wanted to point out my own solution for the Gimp problem (cursor not being released from window), which was reported by sutech some time ago. I will start saying that my xorg.conf has two copies of each device (stylus, eraser and cursor), one for making the tablet act as a pressure device and one to look like a simple mouse. I found this hint on another guide some time ago, but I don't think it has much to do with the Gimp trick.
The main point is the SendCoreEvents statement at the end of xorg.conf. If you assign it to your devices (again: stylus, eraser and cursor), the tablet behaves correctly in the Gimp except that, once you started drawing, you can't release the cursor from its window unless you press the Windows key (right of AltGr) on your keyboard. If you don't add the SendCoreEvents, everything is fine apart from a progressive cursor offset, which is more noticeable if you move away from the center (it is as if you were in Windowed mode instead than in Screen, but no window boundaries in xorg.conf have helped me).
After tinkering with xorg.conf, I found a solution which worked well for me: I removed the CorePointer statement from my PS/2 mouse, and left the SendCoreEvents to the Wacom tablet. I believe the Core events were clashing between mouse and tablet... anyway, everything is working perfectly since then.

I don't know if this applies to Dapper Drake and I will probably never know, as this release seems to be plagued with too many bugs and I really don't want to upgrade just to have to do everything again. :) 

Cheers,

hirumono

---

### Post by Sambalbai on 2006-08-04
Hi all,

Thanks to the quides at the start of this thread I got my Graphire4 running, pressure sensing and all. Great! But I ran into a problem after that: the two buttons and scrollwheel at the top of the tablet won't work. I tried googling around for this, but didn't find anything useful. Did any of you get their buttons/scollwheel working?

grtz,
        Sambalbai

---

### Post by indigoshift on 2006-08-06
> **flaimo said:**
> bump.

can't believe that nobody has changed their buttons on the pen &#8230;

I disable mine, actually.  I always click them on accident when I'm drawing.  ;)

---

### Post by TuxCrafter on 2006-08-07
You have to take a look at the linux wacom site. and the tool xinput and the driver options. I have a wacom 3.

---

### Post by daller on 2006-08-07
> **MetalMusicAddict said:**
> THE HOWTO ITSELF!!! - Shorted :D

Well, MetalMusicAddict...

Could I maybe talk you into creating a wiki-page?

I have made a collection of tablet-setup-howto's here:

[https://wiki.ubuntu.com/TabletSetup](https://wiki.ubuntu.com/TabletSetup)

The TabletSetupWacom is dedicated to the wacom-driver.

But you should probably look into the Wizardpen-driver-wiki, and use UDEV to find the tablet!

Asking people to search through all event* is not that great!

(Simply copy the "Setting up udev"-section!)

One thing, though: Does your setup enable X to start without the tablet connected?

---

### Post by daller on 2006-08-07
Is a serial tablet always connected to /dev/ttyS0 ???

Your guide doesn't tell anything about how to find the right tty!

My wiki-page lacks this too!

---

### Post by FrankL on 2006-08-31
I got a Toshiba Tecra M7 tablet PC and the pen is actually working, thanks to this howto. Thanks!

But I also want the button on my pen to do something. I would like it to work as a right mouse button. Now it just doesn't have any real function.

Any idea how I can activate it? Thanks in advance!

---

### Post by ujecrh on 2006-09-10
Has anyone managed to make the wacom tablet work with Wine or CXOffice in Edgy?

It used to work fine with breezy (I skipped Dapper), Wintab allowed Photoshop to work with pressure sensitivity etc. but not anymore with Edgy.

(I know my tablet is properly configured because Gimp or Krita work perfectly with pressure sensitivity and all but any application I tried under wine seems to see the tablet as a mouse...)

---

### Post by ujecrh on 2006-09-11
Disregard my last message, it is now working. Must have been a glitch between two edgy updates.

---

### Post by MetalMusicAddict on 2006-09-11
> **ujecrh said:**
> Disregard my last message, it is now working. Must have been a glitch between two edgy updates.

So your workin just fine in Edgy? I havnt been able to install it yet.

---

### Post by ujecrh on 2006-09-11
Yes, it worked pretty quickly for me (it took less time than for Breezy for sure). 

Using a Graphire3 I just had to change:
     Option        "Device"        "/dev/wacom"
to:
     Option        "Device"        "/dev/input/wacom"
in /etc/X11/xorg.conf.

The only remaining problem is the mouse wheel which is inverted (goes up when you scroll down) but I have read there is no solution for that yet (the old ZAxisMapping trick is useless).

As for the issue with Wine I mentioned in my first post it seems to be a temporary effect. Typically, if I run Photoshop under Wine right away the tablet does not work but running it again later everything is fine. I will keep investigating.

---

### Post by tempo500 on 2006-09-17
hi,

i am having difficulties setting up my intuos1 serial device! 
until now i used:

/dev/ttyS0
/dev/ttyS1
changed mice to mouse0
deleted the #comments

i really hope someone can come up with a solution or at least a hint!
should i get into the trouble of compiling a new wacom driver? would this help?

thanks in advance! phil

ps.: i am using ubuntu edgy!

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"         
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Driver		"ati"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by jurgnn on 2006-09-22
I have problems with 2.6.18 kernel and dev 0.7.5-3 drivers, logs are fine, tablet is found and driver is loaded, but nothing happens when I try to move pen.

Can't find any useful info with google, except that wacom devices get blacklisted with new kernel, but I dont fully understand what that means.
If anyone got wacom working with 2.6.18 kernel, please gimme some help.

Tablet is volito2 and here is some more info

dmesg | grep wacom
> 
usbcore: registered new driver wacom
drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver

more /var/log/Xorg.0.log | grep wacom
> (II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(**) stylus device is /dev/input/wacom
(**) Option "Device" "/dev/input/wacom"

more /proc/bus/usb/devices
> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056a ProdID=0062 Rev= 2.00
S:  Manufacturer=WACOM
S:  Product=CTF-420 V2.0-0
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 40mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=wacom
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

lsmod | grep wacom
> wacom                  16384  0 
usbcore               129504  5 usbhid,wacom,ehci_hcd,uhci_hcd

---

### Post by TuxCrafter on 2006-09-22
Try to check if the events are still responding with the wacom device  (first post) 

And try to remove the wacom driver from the blacklist.

This is al I can think off.

The new kernel did not work with my acpi on my via epia en12000 board to. some people told me that you can't use stock kernels but you have to use ubuntu kernels because they are different.

some links:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

I haven't tried out those things on the links. I always had success with stock kernels before this kernel.

---

### Post by jurgnn on 2006-09-23
> **TuxCrafter said:**
> Try to check if the events are still responding with the wacom device  (first post) 
And try to remove the wacom driver from the blacklist.

Nope, its not responding and I don't know how to remove driver from blacklist or is it even possible.

[http://mm-traffic.lieberbiber.de/node?page=4]("http://mm-traffic.lieberbiber.de/node?page=4")
> If we let HID ignore all wacom devices, wacom driver will be the one to take control of the devices. In the case that a new device added before wacom driver supports it, it will be easier to just build a stand alone module, wacom.ko, than to build usbhid or sometime even builtin.o for hid-core.c. Right now, this is the most complaints we got from end users who try to upgrade wacom driver.

---

### Post by TuxCrafter on 2006-09-23
Can't help you out. I don't like the wacom driver so I will not put my time in it. I went back to the 2.6.17.13 kernel.

---

### Post by tog on 2006-10-15
I have an Intuos3 4x6 tablet (the new one), and I am having a difficult time trying to get it working properly. 

The problem is that once I go to configure extended input devices in GIMP, I get the message that > there are no extended input devices.

I have a suspicion that even though the wacom driver is being loaded, somehow the tablet is being recognized only as a mouse. I have changed the udev rules so that the wacom rule gets loaded earlier. That is, instead of 45-wacom, it now reads 20-wacom. I have also put wacom in /etc/modules, but to no avail. Any help/suggestions would be appreciated.

My configuration:

OS: Ubuntu Edgy - 2.6.17-10
wacom-tools        0.7.2-0ubuntu7 

Output of dmesg | grep wacom
```
[17179606.576000] usbcore: registered new driver wacom
[17179606.576000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver

```
I also get the following for dmesg | grep Tablet
```
[17179835.080000] input: Tablet PTZ-431W as /class/input/input5
[17179835.080000] input,hiddev96: USB HID v1.00 Mouse [Tablet PTZ-431W] on usb-0000:00:1f.2-2

```

My xorg.conf file:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option        "PressCurve"    "50,0,100,50"
  Option        "Mode"          "Absolute"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" 
  Option        "Type"          "eraser"
  Option        "USB"           "on"
  Option        "Mode"          "Absolute"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
  Option        "Mode"          "Relative"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "pad"
  Option        "USB"           "on"                
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "AlwaysCore"
        InputDevice     "cursor" "AlwaysCore"
        InputDevice     "eraser" "AlwaysCore"
        InputDevice     "pad"
EndSection


```

Output of more /var/log/Xorg.0.log | grep wacom
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(**) stylus device is /dev/input/wacom
(**) cursor device is /dev/input/wacom
(**) eraser device is /dev/input/wacom
(**) pad device is /dev/input/wacom
(**) Option "Device" "/dev/input/wacom"
(**) Option "Device" "/dev/input/wacom"
(**) Option "Device" "/dev/input/wacom"
(**) Option "Device" "/dev/input/wacom"

```

---

### Post by MetalMusicAddict on 2006-10-15
You wouldnt happen to be using XGL would you? There are problems with wacom pads and XGL.

---

### Post by tog on 2006-10-15
To add to my earlier (above) post, it looks like usbhid is taking over the tablet rather that wacom. Here is the output of cat /proc/bus/usb/devices 
```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056a ProdID=00b7 Rev= 1.16
S:  Manufacturer=Tablet
S:  Product=PTZ-431W
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=  10 Ivl=4ms

```

---

### Post by tog on 2006-10-15
No, I don't have XGL. I think that usbhid is taking over the tablet, rather than wacom.

Thanks for your reply.
> **MetalMusicAddict said:**
> You wouldnt happen to be using XGL would you? There are problems with wacom pads and XGL.

---

### Post by tog on 2006-10-15
Well, I at least found one solution. I recompiled the wacom.ko module after downloading the source from  [http://linuxwacom.sf.net](http://linuxwacom.sf.net). But, plugging in the tablet still loads the usbhid module. I then removed the usbhid module, modprobe wacom, and restarted X. I can now get the GIMP to use the extended input devices.

---

### Post by P_Badger on 2006-10-24
> **graigsmith said:**
> prokoudine, you don't need to determine what event the device is on, let wacom-tools do the work of finding and creating a link to your tablet.

install the package wacom-tools

change the device from event4 to /dev/input/wacom

also remove comments at the end of the wacom device lines.  that messes things up, if anything move them to the next line. or just delete them.

when you are finished your wacom section in your xorg.conf file should look like this. if it is a usb tablet.

```

#Wacom Section

Section "InputDevice"
	Identifier "cursor"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "cursor"
	Option "USB" "on"
	Option "Mode" "Relative"
EndSection

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "USB" "on"
	Option "PressCurve" "50,0,100,50"
	Option "Mode" "Absolute"
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "eraser"
	Option "USB" "on"
	Option "Mode" "Absolute"
EndSection

```

dont forget to add the last 3 things to your server layout section.
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice "cursor" "AlwaysCore"
	InputDevice "stylus" "AlwaysCore"
	InputDevice "eraser" "AlwaysCore"
EndSection

``` 
after that reboot and it should work.

Just want to thank you, as I've tried several ways to get my wacom working properly, but following your directions EXACTLY made my Graphire3 usb work 100% in Gimp. I was having a horrid time getting the eraser to work *at all*.

---

### Post by flaimo on 2006-11-03
i'm still looking for more information on [how to change the mapping]("http://www.ubuntuforums.org/showpost.php?p=1184680&postcount=92") of the buttons on the pen. i want the default behavior like in windows.

---

### Post by Ryupower on 2006-11-17
Why does my xserver keep on getting screwed up?
I replace the already existent default wacom lines ( which my graphire4 won't work under,correctly ) in my xorg and restart.
Then it can't ever load the xserver! I always have to replace it by doing   sudo dpkg-reconfigure xserver-xorg. I tried 3 times, following the given instructions carefully, but it still does that.

what am I doing wrong?

---

### Post by finferflu on 2006-11-23
> **MetalMusicAddict said:**
> You wouldnt happen to be using XGL would you? There are problems with wacom pads and XGL.

I've been using this tutorial and it worked on Dapper. As far as I remember it has worked also on Edgy. The only thing is that now it's not working anymore, and I've recently installed Beryl/XGL. 

Is there any way to make it work either with or without XGL (i.e. having XGL installed but not using it when using the pet tablet, if possible)?


Thank you.

---

### Post by tempo500 on 2006-11-23
> **flaimo said:**
> i'm still looking for more information on [how to change the mapping]("http://www.ubuntuforums.org/showpost.php?p=1184680&postcount=92") of the buttons on the pen. i want the default behavior like in windows.

just ad this line to your sessions found in system/preferences/sessions - tab "startup programs"

```
xinput set-button-map Wacom_Stylus 1 3 2
```

and install xinput with synaptic

greets, philip

---

### Post by finferflu on 2006-11-24
No joy!

Since I've installed Beryl/XGL, my pen tablet stopped working. I've just uninstalled it, but still no joy.

I've got wacom-tools installed and if I do **sudo wacdump /dev/input/wacom** I get this:

```
MODEL=Wacom Volito2 4x5                 ROM=2.0-0
CLS=USB  VNDR=Wacom  DEV=Volito2  SUB=CTF-420-U




TOOLTYPE=NONE                            IN_PROX=+00000 (+00000 .. +00000)
  BUTTON=+00000 (+00000 .. +00000)         POS_X=+00000 (+00000 .. +05104)
   POS_Y=+00000 (+00000 .. +03712)      DISTANCE=+00000 (+00000 .. +00032)
PRESSURE=+00000 (+00000 .. +00511)      RELWHEEL=+00000 (-00001 .. +00001)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=   
``` 

Which means that it is recognised, but when I move the pen, no input. I've also checked with /dev/input/event#, and I've found it on event4 too:

```
MODEL=Wacom Volito2 4x5                 ROM=2.0-0
CLS=USB  VNDR=Wacom  DEV=Volito2  SUB=CTF-420-U




TOOLTYPE=NONE                            IN_PROX=+00000 (+00000 .. +00000)
  BUTTON=+00000 (+00000 .. +00000)         POS_X=+00000 (+00000 .. +05104)
   POS_Y=+00000 (+00000 .. +03712)      DISTANCE=+00000 (+00000 .. +00032)
PRESSURE=+00000 (+00000 .. +00511)      RELWHEEL=+00000 (-00001 .. +00001)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=    
```

So the problem is not even with xorg.conf, it's just that my system is not able to receive my pen tablet's impulses, I think.

Any suggestions?

Thanks!

---

### Post by finferflu on 2006-11-26
Well, the problem was not actually XGL, but a bug with Edgy for Volito2.

I've sorted it out, here's the thread for those who might need it: [http://www.ubuntuforums.org/showthread.php?t=306874](http://www.ubuntuforums.org/showthread.php?t=306874)

Hope it helps!

---

### Post by richardq on 2006-11-27
I'm having problems with my Graphire3 tablet. It used to work in Dapper and I think I had it working in Edgy a while back but now I have no luck. Here is the problem:

The tablet is recognized and the pointer moves. In the GDM login screen the tablet moves the cursor over the whole screen extents. However once I log in it's movement is limited only to a portion of the screen. Also, no extended input devices are recognized in the GIMP.

I've read (and re-read) the threads here and tried a bunch of things - none of them seem to correct the problem. 

The tablet is USB. I've tried it both under Beryl and under Metacity with no difference. Here is my current xorg.conf file. Any help would be greatly appreciated:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option        "Mode"          "Absolute"
  Option        "PressCurve" "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "USB"           "on"
  Option        "Mode"          "Absolute"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "Mode"          "Relative"
  Option        "USB"           "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option "XAANoOffscreenPixmaps" "true"

EndSection

Section "Monitor"
	Identifier	"VE910-3Serie"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"VE910-3Serie"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

        # Enable 32-bit ARGB GLX Visuals
        Option "AddARGBGLXVisuals" "True"

        # If you are using an older version of compiz that
        # does not support rendering into the Composite
        # Overlay Window, you will need to disable clipping
        # of GLX rendering to the X Root window with this
        # option, or you will get a blank screen after
        # starting compiz:
        #  Option "DisableGLXRootClipping" "True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection


```

---

### Post by richardq on 2006-11-28
This morning it seems to be working! Is it possible that a reboot is different than a Ctrl-Backspace to restart X? 

Anyway, the last change I made (I believe) was to eliminate the '#For Tablet PC Only' lines. Although I never had to remove these before. I'm not 100% sure that was the problem, but it was likely the last change I made.

Hopefully this is the end of it.

---

### Post by finferflu on 2006-11-28
I think rebooting was pretty much the solution...

---

### Post by TuxCrafter on 2006-11-28
> **richardq said:**
> This morning it seems to be working! Is it possible that a reboot is different than a Ctrl-Backspace to restart X? 

Anyway, the last change I made (I believe) was to eliminate the '#For Tablet PC Only' lines. Although I never had to remove these before. I'm not 100% sure that was the problem, but it was likely the last change I made.

Hopefully this is the end of it.

This is because the udev system has to detect your wacom device for xorg restart xorg will not do this. If you also had restart the udev system it will work but a reboot will do this trick to.

---

### Post by Roostey on 2006-12-11
> **Sambalbai said:**
> Hi all,

Thanks to the quides at the start of this thread I got my Graphire4 running, pressure sensing and all. Great! But I ran into a problem after that: the two buttons and scrollwheel at the top of the tablet won't work. I tried googling around for this, but didn't find anything useful. Did any of you get their buttons/scollwheel working?

grtz,
        Sambalbai

I had the same problem with a Graphire 4.  The solution was to add ButtonsOnly, Button9 and Button13 to the InputDevice for the pad.  The scrollwheel is inverted though.

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "ButtonsOnly" "on"
  Option        "Button9" "1"
  Option        "Button13" "3"
  Option        "Device" "/dev/input/wacom"
  Option        "USB" "on"
  Option        "Type" "pad"
EndSection
```

---

### Post by moaxey on 2006-12-21
i've been trying to enable my wacom with edgy on a macbook with a dual screen xinerama setup, that is pretty much the same as described here 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

so I've been following these instructions on top of that.

things kind of work, but i have some unusual problems:
[LIST]
[*]the wacom cursor doesnt follow the Above RightOf command, and only operatesas RightOf (not what i want), although my other mouse cursor does (Above).
[*]when i enable pressure sensitivity in inkscape or gimp, it works, but offsets the cursor by quite a lot, leading to a situation where i cannot draw in entire document without clicks being recognised outside. When i disable pressure sensitivity, the location of the cursor is correct.
[*]i can only ctrl-alt-delete once, and the second time i get an unknown error on my xserver, where it is looking for a display that is never actually referenced; and restarting without making any changes gives me a successful startup
[/LIST]

any clues on any of these problems would be appreciated

---

### Post by davim on 2006-12-28
Hi! I have a wacom graphire4 and its working fine in edgy!
But I can't get it to work with XGL. Does any one have a tablet working with XGL enabled? I think the problem might be in the screens used by XGL.

---

### Post by finferflu on 2006-12-28
It is a known problem that Wacom and XGL don't go together. I had to give up to Beryl for that :(

---

### Post by richardq on 2006-12-28
> **davim said:**
> Hi! I have a wacom graphire4 and its working fine in edgy!
But I can't get it to work with XGL. Does any one have a tablet working with XGL enabled? I think the problem might be in the screens used by XGL.

I have my Graphire3 working with Beryl/AIGLX in Edgy. No problems so far (Except that Beryl takes away a few of the nice mouse shortcuts in Inkscape.. :( ) I'm not sure if it's an XGL specific (as opposed to AIGLX) problem, but it *is* working fine on my machine.

My Xorg.conf file was posted [right here]("http://ubuntuforums.org/showthread.php?p=1816074#post1816074") in this thread a few weeks back.

Good luck.

---

### Post by davim on 2006-12-29
Thanks! I think you have it working with beryl because you are using AIGLX and not XGL (dam ATI sucks :( ) I gess I'll have to give up on beryl when I want to use my tablet.

BTW: I have my pad's buttons and scroll working with this: [http://foto-cs.de/blog/item/196](http://foto-cs.de/blog/item/196) but isn't there a way to do this just with xorg, without a program running in background?

---

### Post by el_ricardo on 2007-01-22
THANKYOU SO MUCH!!!!!

I was about to give up hope with this, all the other howtos i've found involve stupid kernel settings and stuff, I actually use fedora, but when i saw a howto merely involving a xorg.conf edit here I almost cried with joy!

edit- davim, I found that the scroll wheel works if you add this to your xorg.conf:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/event4" **<---or whatever yours is**
  Option        "Type"          "pad"
  Option        "USB"           "on"               
  [b]Option        "ButtonsOnly"   "on"
  Option        "Button9"       "2"
  Option        "Button13"      "3"[/b]
EndSection

```

also, add 

```
InputDevice    "pad"       "SendCoreEvents"
```

to the server layout section, i know MetalMusicAddict's howto said not to, but my scroll wheel didn't work without that option

---

### Post by erolerten on 2007-02-15
After installing what graigsmith had suggested, I tried to add the codes, Metalmusicaddict had written.

In my xorg.conf file ther were lines containing wacom already. Is that normal?

I coul also not save the file after editing in GEDIT. Ubuntu said that I was not permitted to edit this file. Do I have to use another editor?

I probably do not need to add that I am a complete beginner.
Please help.

---

### Post by richardq on 2007-02-15
> **erolerten said:**
> After installing what graigsmith had suggested, I tried to add the codes, Metalmusicaddict had written.

In my xorg.conf file ther were lines containing wacom already. Is that normal?

I coul also not save the file after editing in GEDIT. Ubuntu said that I was not permitted to edit this file. Do I have to use another editor?


I'm not sure what version of Ubuntu you are running, but I think the Wacom support was included in Edgy already so Xorg might have already contained the wacom lines.

As far as editing the xorg.conf file, you have to open it as root or else it will only let you read (and not modify) the file. To do this, start up a terminal and run gedit using:

sudo gedit

or 

gksudo gedit


It will ask you for your password and then it will open gedit as root and you should be able to open, modify and save the xorg.conf file.

---

### Post by erolerten on 2007-02-19
Thank you very much.




> **richardq said:**
> I'm not sure what version of Ubuntu you are running, but I think the Wacom support was included in Edgy already so Xorg might have already contained the wacom lines.

As far as editing the xorg.conf file, you have to open it as root or else it will only let you read (and not modify) the file. To do this, start up a terminal and run gedit using:

sudo gedit

or 

gksudo gedit


It will ask you for your password and then it will open gedit as root and you should be able to open, modify and save the xorg.conf file.

---

### Post by MetalMusicAddict on 2007-02-24
Ive updated the HOW-TO some. If there's anything out of place please let me know.

---

### Post by jay_knight on 2007-02-26
Got it working: switching from XGL to AIGLX did the trick. 

However: when I use the tablet as a mouse, it behaves strangely. That is, when moving the pen to the edge of the tablet, the cursor stops moving before reaching the edge of the screen (about 1 cm off, but this seems to vary upon the speed at which I moved the pen). It is only when I move the pen very slowly the cursor actually reaches the edge of the screen. This is undesirable for 'office/mouse' use.

Does someone recognize the problem and/or know a solution?

Thanks! 
J.

---

### Post by CyBuzz on 2007-03-03
I cant seem to find the drivers on the wacom site.

I have an Intuos3 USB and I have my mouse working, though there are issues.  Looks like the pen works fine in Gimp, Inkscape and Krita

1.  Scroll is inverted
2.  the buttons on the sides of the mouse dont work.
3.  Before the mouse will work, I need to touch the pen to the pad before the mouse will work.

I have wacom-tools, wacom-kernel-source and xserver-xorg-input-wacom installed.

Here is my xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/wacom"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option	"USB"		"on"
#  Option        "ForceDevice"   "ISDV4"           
  Option 	"PressCurve"	"50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option	"USB"		"on"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option	"Mode"		"relative"
  Option	"USB"		"on"
  Option	"ZAxisMapping"	"4 5"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
#  Option        "ButtonsOnly" "on"
#  Option        "Button9" "2"
#  Option        "Button13" "3"
  Option        "Device" "/dev/input/wacom"
  Option        "USB" "on"
  Option        "Type" "pad"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
#	InputDevice    "pad"       "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by MetalMusicAddict on 2007-03-03
Just to make sure, it is a USB model right? Whats the model?

---

### Post by CyBuzz on 2007-03-03
Yeah, Intuos3 USB

---

### Post by Commodore Guff on 2007-03-11
Hi.  After trying multiple proposed solutions here, I still can't get my Intuos3 USB tablet working correctly.  It recognizes the pen and the mouse, but the precision of both is very, very poor.  By that I mean that the minimum amount that I can actually move the pointer is around 3 pixels.  Pressure sensitivity is not working, and none of my graphics programs recognize any extended input devices.

I am running Ubuntu Edgy, and I have the Wacom tools package installed.  My graphics card is Nvidia, and I've tried to get the tablet working on both Beryl and GNOME, but no luck.  I hope that is sufficient information.

Thanks.

---

### Post by MetalMusicAddict on 2007-03-11
Can you please post your xorg.conf?

---

### Post by Commodore Guff on 2007-03-11
> **MetalMusicAddict said:**
> Can you please post your xorg.conf?
This is the most recent one I tried.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "L1732TQ"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "L1732TQ"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by MetalMusicAddict on 2007-03-11
WOW! No wonder your having issues. You have multiple entries that Im sure are messing you up.

Give me a couple of mins to clean this up.

---

### Post by MetalMusicAddict on 2007-03-11
Try this:

```
[SIZE="1"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load 	"dbe"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "Monitor"
    Identifier     "L1732TQ"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "L1732TQ"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection[/SIZE]
```

---

### Post by Commodore Guff on 2007-03-11
> **MetalMusicAddict said:**
> WOW! No wonder your having issues. You have multiple entries that Im sure are messing you up.

Give me a couple of mins to clean this up.

Didn't even notice that.

Just keep in mind that I've tried multiple configurations, and I know that the others didn't have multiple entries like that.

---

### Post by Commodore Guff on 2007-03-12
> **MetalMusicAddict said:**
> Try this:

```
[SIZE="1"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load 	"dbe"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "Monitor"
    Identifier     "L1732TQ"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "L1732TQ"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection[/SIZE]
```

I have that exact configuration saved now, but I'm still having the same issues.

---

### Post by MetalMusicAddict on 2007-03-12
Ok. Everything else still works but the pen right? Can I have a link to your exact tablet?

---

### Post by Commodore Guff on 2007-03-12
> **MetalMusicAddict said:**
> Ok. Everything else still works but the pen right? Can I have a link to your exact tablet?

What do you mean by "everything else?"

Erm, you mean [this?]("http://www.wacom.com/intuos/4x6.cfm")

---

### Post by MetalMusicAddict on 2007-03-12
> **Commodore Guff said:**
> What do you mean by "everything else?"Meaning the other things controlled by your xorg. I'm guessing yes because your not screaming about mouse or display issues. ;)
> Erm, you mean [this?]("http://www.wacom.com/intuos/4x6.cfm")
Yes.

What the version of your kernel? Also [THIS]("http://linuxwacom.sourceforge.net/") site might also provide help.

---

### Post by Commodore Guff on 2007-03-12
> **MetalMusicAddict said:**
> Meaning the other things controlled by your xorg. I'm guessing yes because your not screaming about mouse or display issues. ;)

Yes.

What the version of your kernel? Also [THIS]("http://linuxwacom.sourceforge.net/") site might also provide help.

Oh, okay.

Uh, I guess it's just the generic 2.6.17.11 kernel.

Okay, I'm trying that now.  Not entirely sure as to what I'm doing, but hey, it feeds my sense of adventure.:)

---

### Post by Commodore Guff on 2007-03-12
Still not working, and it seems like I set up the Linux wacom thing correctly.

---

### Post by MetalMusicAddict on 2007-03-13
> **Commodore Guff said:**
> Still not working, and it seems like I set up the Linux wacom thing correctly.

Yeah. From the looks of things things its set up right. So now I look elsewhere.

Are you running Dapper (6.01) or Edgy (6.10)? If its Edgy are you completely up-to-date? Ive been running Feisty so long I forget what the current kernel is in Edgy.

---

### Post by Commodore Guff on 2007-03-13
> **MetalMusicAddict said:**
> Yeah. From the looks of things things its set up right. So now I look elsewhere.

Are you running Dapper (6.01) or Edgy (6.10)? If its Edgy are you completely up-to-date? Ive been running Feisty so long I forget what the current kernel is in Edgy.

Edgy.  And yes, completely up-to-date.

---

### Post by MetalMusicAddict on 2007-03-13
> **Commodore Guff said:**
> Edgy.  And yes, completely up-to-date.

Man. Im sorry to say that it looks like the wacom-tools package in Ubuntu (Feisty) is only 0.7.2 where you need 0.7.6-4. :( Meaning, it wouldnt be in Edgy either.

Im going to look into getting this done for Feisty but dont count on it. Im sorry man. Ill do the best I can. Keep the config. Maybe Ill get a wacom-tools .deb made up to solve this.

---

### Post by Commodore Guff on 2007-03-13
> **MetalMusicAddict said:**
> Man. Im sorry to say that it looks like the wacom-tools package in Ubuntu (Feisty) is only 0.7.2 where you need 0.7.6-4. :( Meaning, it wouldnt be in Edgy either.

Im going to look into getting this done for Feisty but dont count on it. Im sorry man. Ill do the best I can. Keep the config. Maybe Ill get a wacom-tools .deb made up to solve this.

Anyway I could just compile it myself? :confused:

---

### Post by MetalMusicAddict on 2007-03-13
> **Commodore Guff said:**
> Anyway I could just compile it myself? :confused:

Sure. I think the 2 packages you would need to redo are **wacom-tools** and **xserver-xorg-input-wacom**.

---

### Post by Commodore Guff on 2007-03-13
> **MetalMusicAddict said:**
> Sure. I think the 2 packages you would need to redo are **wacom-tools** and **xserver-xorg-input-wacom**.

Uh, sorry, but any tips on where to find the first one?:confused:
Erm, and the second, I guess.

---

### Post by MetalMusicAddict on 2007-03-13
> **Commodore Guff said:**
> Uh, sorry, but any tips on where to find the first one?:confused:
Erm, and the second, I guess.

I actually couldnt tell you since I would have someone else do it for me as well. :(

---

### Post by Commodore Guff on 2007-03-13
> **MetalMusicAddict said:**
> I actually couldnt tell you since I would have someone else do it for me as well. :(

Eh, it's okay.

Still not turning up anything, though.:confused:

---

### Post by CyBuzz on 2007-03-14
Ok, I think I have most of this working.  Here are my final issues I am still researching:

1.  Side buttons on mouse dont work
2.  Mouse will not work unless I touch the pen to the pad first.

I am sure that there are some others that I will find as I use it more, but those are the ones that stick out.

I found everything I needed in these forums....not necessarily in this thread, but in the ubuntuforums.

Man I love this distro.  I havent been this happy with a distro since Gentoo.

---

### Post by MetalMusicAddict on 2007-03-14
Can you give the Wacom model and Ubuntu version with kernel your using?

---

### Post by CyBuzz on 2007-03-14
> **MetalMusicAddict said:**
> Can you give the Wacom model and Ubuntu version with kernel your using?

Intuos3 and I am using Ultimate Ubuntu Edition 1.2 with the default ( .11 I think) kernel

I can double check that tonight when I get home from work.

---

### Post by MetalMusicAddict on 2007-03-14
CyBuzz your in the same boat with Commodore Guff I believe with your Intuos3.

I also dont know what if anything Ultimate Ubuntu Edition 1.2 has done. I dont use it nor do I recommend it.

---

### Post by CyBuzz on 2007-03-14
I like it.  Alot of things 'just work' with it that didnt with standard Ubuntu.  I guess I will have to figure out how to troubleshoot or set another machine to test on.

---

### Post by CyBuzz on 2007-03-18
Ok,

I installed standard Edgy and got everytheing working....except the scroll wheel, it is inverted.  There was a howto but I cant find it now.  It had you do something like set xsetwacom and save it in a hidden file.  Well, i forgot to save that hidden file and now cant find the solution.

I also need to figure out how to set the pad buttons and the buttons on the sides of the mouse.

After that, I am done with the wacom setup and can move to whatever I find to be the next problem:)

Also..this is odd to me, but may be ok since I dont know what the list means.
jeff@springfield:~$ xsetwacom list
pad              unknown   <----
cursor           cursor    
eraser           eraser    
stylus           pad      <---

---

### Post by CyBuzz on 2007-03-18
All right here is the deal. I did the following in order.

```

Install Ubuntu 6.10
Add Universe and Multiverse Repositories
Update
Install ntfs-3g
apt-get update
apt-get install -y ntfs-3g libfuse2 fuse-utils ntfstools
echo fuse | sudo tee -a /etc/modules
addgroup ntfs
modprobe fuse
apt-get clean
apt-get autoclean
Install wacom-tools
apt-get install -y wacom-tools
restart X
disable ipv6 system wide
/etc/modprobe.d/blacklist-ipv6
Add blacklist ipv6
Install Envy
apt-get install envy
Run Envy
Reboot

```

right before disabling IPV6 everything worked except for the inverted scrolling and side buttons.  The thing I am really concerned with is that the mouse worked when I restarted X

I installed envy (and installed NVIDIA drivers) and rebooted.  Once rebooted, the mouse didnt work until I touched the pen to the pad.  Then it worked fine barring inverted scrolling and side buttons.

I am guessing that either Envy or Nvidia is to blame.  I just dont know what I will do.  I didnt reboot after doing the wacom-tools thing, I just restarted x.

I dont really want to do another clean install.  Unless someone has some ideas, I will just have to live with the pen first thing.

---

### Post by chocobo_ff on 2007-03-28
Hi MetalMusicAddict,

First of all I want to thank you for the great guide you have made! I think it's a really helpful and much easier to understand guide than the official linuxwacom one. Just wondering if you have an estimated timeline for when you'll be free to make that .deb package for version 0.7.6-4? I'm struggling to compile that in Kubuntu Edgy (for both the original 2.6.17-11 kernel and 2.6.20-4 kernel which I upgraded to later). The reason I'm asking is because I'm trying to set up a Intuos3 4x6 and I think that's the driver version I need?

Thanks again for your great effort and hope you will continue to contribute to this HOWTO!! :)

---

### Post by MetalMusicAddict on 2007-03-28
> **chocobo_ff said:**
> Hi MetalMusicAddict,

First of all I want to thank you for the great guide you have made! I think it's a really helpful and much easier to understand guide than the official linuxwacom one. Just wondering if you have an estimated timeline for when you'll be free to make that .deb package for version 0.7.6-4? I'm struggling to compile that in Kubuntu Edgy (for both the original 2.6.17-11 kernel and 2.6.20-4 kernel which I upgraded to later). The reason I'm asking is because I'm trying to set up a Intuos3 4x6 and I think that's the driver version I need?

Thanks again for your great effort and hope you will continue to contribute to this HOWTO!! :)

Im gonna have to talk to our packagers. See whats involved. I cant really give a timeline.

If we have to do kernel work beyond a simple new "wacom-tools" or so it probably wont happen. :(

I might be able to file a bug but its a new upsream version and it would take a exception. I also think since this is in Main it would take a miracle.

Ill look into it.

---

### Post by chocobo_ff on 2007-03-28
Ok well at least it's good to know this problem is being looked into :)

I'm going to keep trying this weekend when I have more time and will keep an eye out for any updates in this thread. From reading through most of this thread, I found that tog have managed to get his Intuos3 4x6 working in [this section of the thread]("http://ubuntuforums.org/showthread.php?t=25151&page=12"), but haven't been able to get hold of him to get more help. :( Maybe I'll try spending a bit more time reading the linuxwacom documentation. The first time I did that I was quite lost, but hopefully with more time to spend during the weekend I'll be able to sort it out :)

---

### Post by bren21 on 2007-03-29
Hi, I have been trying to get my Graphire 4 working on Edgy, I followed your tutorial however it did not seem to work.  I have to press the pen to the tablet in order to get it to move and tap it twice quickly in order to get it to click anything.  Basically it is working like a touchpad (I am using a laptop so I am not sure if this  has something to do with it?) Any help  I could get would be appreciated.

---

### Post by Mr.Slappy on 2007-03-31
> **Commodore Guff said:**
> Uh, sorry, but any tips on where to find the first one?:confused:
Erm, and the second, I guess.

Hi Commodore Guff,

[http://packages.qa.debian.org/w/wacom-tools.html](http://packages.qa.debian.org/w/wacom-tools.html)
Hope this helps.

---

### Post by MetalMusicAddict on 2007-04-02
Anyone using Feisty and having issues with their Wacom pads "wacom-tools" has just been updated to the 0.7.7-7 development version so this should add support for newer pads as well as features of other pads.

Please chat here if this has helped some people.

[The Linux Wacom Project]("http://linuxwacom.sourceforge.net/")

---

### Post by gordebak on 2007-04-06
Hi, I use Feisty. My Wacom Volito 2 was detected well out-of-the-box. After installing wacom-tools package pressure sensitivity is working ok.

---

### Post by Pitel on 2007-04-07
Hi,
I've installed those 2 Wacom packages, and It doesn't work. It connects as USB device /dev/input/wacom, but when I use wacdump on it, it tells me that Volito2 is connected, but when I use my stylus, it does nothing. So messing with xorg.conf has no sense.
Pls help, it works on my Fedora desktop.

---

### Post by locke.dragon on 2007-04-07
i followed your directions and then restarted x and it gave me the equivalent of the blue screen of death saying it couldn't start x server.  could you tell me how to fix this?  i'm using windows to write this post right now.  -barfs-

scratch that.  fixed it a while back.  just forgot about this thread.  :P

---

### Post by Mikebgr on 2007-04-21
Hello everyone! My wacom is working perfectly, except this minor bit. Before I upgraded to 7.04, everything was fine.
 Although, my scroll wheel was inverted before, upgrade, I just did 
```
xmodmap -e "pointer = 1 2 3 5 4"  
```on startup and it worked perfect. But now my wheel is inverted again, and playing around with xmodmap wont fix the problem! Any suggestions?

edit: my tabled is CTE-430 (sapphire)

---

### Post by finferflu on 2007-04-24
Sorry if this has already been asked earlier on, but I didn't follow the whole thread.
Is there any way to get the pen tablet working properly without restarting X every time?

Thanks.

---

### Post by MetalMusicAddict on 2007-04-24
> **finferflu said:**
> Sorry if this has already been asked earlier on, but I didn't follow the whole thread.
Is there any way to get the pen tablet working properly without restarting X every time?

Thanks.Not that I know of.

---

### Post by finferflu on 2007-04-24
> **MetalMusicAddict said:**
> Not that I know of.
I was thinking about modprobing... no? like ```
modprobe -r wacom
``` and then ```
modprobe wacom
```

???

---

### Post by Amazing Iceman on 2007-04-25
Thanks for this HOWTO... My tablet now works great under 7.04!!!!

Just something I noticed:

- My Xorg.conf file was already configured for the tablet, but instead of pointing the device to /dev/input/wacom, it was pointing it to /dev/wacom.
- After installing wacom-tools and rebooting, still was pointing to /dev/wacom.

That was the only change I had to do manually to get it to work.
I also added the recommended setting to adjust sensitivity.

Maybe this is something that could be automated by the installation on the next release, to please the newcomers?


Thanks again.

--The Amazing Iceman

---

### Post by Affrikka on 2007-05-04
Hey great guide.. but still I need some help..

I got it all installed, and it says its all working, but I can't seem to get it to run, or set it up on the GIMP or anything.. it won't actually *work*

can you help me please?

thanks,

_-=Affrikka=-_

---

### Post by Sladi on 2007-05-09
Hi! 
My Intuos3 works partially. 

I'd like to assign buttons but ```
wacdump ./wacom
``` stopped working. No value changes there. 
Sometimes it gives an error now:
```
Segmentation fault (core dumped)
```

Can someone help please? 

Here is part of my xorg.conf: 
```
Section "InputDevice"
	Identifier  	"stylus"
	Driver      	"wacom"
	Option	    	"Device" 	"/dev/input/wacom"
	Option	    	"Type" 		"stylus"
	Option        	"USB"           "on"
	Option 		"KeepShape" 	"on"
EndSection

Section "InputDevice"
	Identifier  	"eraser"
	Driver      	"wacom"
	Option	    	"Device" 	"/dev/input/wacom"
	Option	    	"Type" 		"eraser"
	Option        	"USB"           "on"
	Option 		"KeepShape" 	"on"
EndSection

Section "InputDevice"
	Identifier  	"cursor"
	Driver      	"wacom"
	Option	    	"Device" 	"/dev/input/wacom"
	Option	    	"Type" 		"cursor"
	Option        	"USB"           "on"
EndSection

Section "InputDevice"
	Identifier	"pad"	
	Driver		"wacom"
	Option  	"Device"     	"/dev/input/wacom"
	Option	        "Type"  	"pad"
	Option        	"USB"           "on"
	Option 		"ButtonsOnly" 	"on"
EndSection
```

---

### Post by hessiess on 2007-05-16
how can i get a volito2 working in ubuntu with no internet conection(internet only works in windows)

---

### Post by AlumaSqrl on 2007-05-18
> **finferflu said:**
> Is there any way to get the pen tablet working properly without restarting X every time?

If you're having problems with the tablet being moved to different event devices and then becoming useless, i always got it to work by unplug/re-plugging the tablet to make udev re-link the /dev/input/wacom device to the proper event device, then i'd end up in a situation where the tablet is then treated as a generic pointer device.  I'd solve this by simply ctrl-alt-F1 to a text console and then ctrl-alt-F7 back to the X session.   After this, the tablet regained the extended device functions and the proper behaviour as defined in the xorg.conf file.  I'm not sure why this is, but it also repairs functionality after doing a modprobe operation on the wacom module. Of course, this may not work for you... as it seems there's a lot of unique problems around this discussion, and i may be completely misinterpreting what you're asking.

good luck

---

### Post by AlumaSqrl on 2007-05-18
Has anyone found a solution to problems such as those described previously by sutech and moaxey?  I'm referring to cases involving cursor offset in GIMP and Inkscape when using a multi-screen server layout.  The cursor and drawing point meet only on the edge of the screen and diverge drastically from there.  Pressure sensitivity and tablet mode options are functional, however.  This, of course, only happens when the application is configured to use the particular extended device.  Otherwise, the tablet behaves normally, but without pressure sensitivity.  

I had very little trouble getting the tablet working properly under Hoary (barring a udev.rules modification), but have had no luck since i've switched to Feisty.  The tablet is a CTE-430-UV3 Graphire 3.  I'm running a triple head setup without xinerama (though the problem persists with xinerama enabled).    I've tried running wacdump or xxd on /dev/input/<udev_generated_link> and the corresponding event device, but it seems that as long as X has control over the device, wacdump can't get any info excepting the model information.  I'm not sure if this is normal, as i seem to recall it working under Hoary.  (maybe i'm wrong on that)

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
       Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device" "/dev/input/tablet-graphire3"
#       Option          "SendCoreEvents" "on"
#       Option          "ScreenNo" "0"
#       Option          "KeepShape" "off"
#       Option          "Twinview" "horizontal"
        Option          "Mode" "Relative"
        Option          "Type" "stylus"
        Option          "USB" "on"
EndSection


```

Within the context of the input device definitions, i've tried the seemingly pertinent options, but "screenno" "keepshape" and "twinview" seem to have no effect... at least none on my particular issue.  

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" rightof "Screen0"
        Screen      2  "Screen2" leftof "Screen0"
        Option         "Xinerama" "off"
#       Option         "Clone" "off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
EndSection
```

As i mentioned, the problem persists with Xinerama enabled.  Actually, it gets worse because of the differing resolutions involved in the screen section.    The only way i can get the problem to go away is to comment out ALL BUT ONE screen.      If anyone has any helpful insight or questions to ask, please let me know .  At this rate, i'll be bald before week's end.

---

### Post by sirarokh on 2007-05-23
I have the same problems with multible screens.

it would even help a lot if it was possible to disable the cursor completely and use the wacom as stylus only.

Or else use the wacom only relative to the (mouse-) cursor position.

---

### Post by sirarokh on 2007-05-23
I did find a solution for our problem:

You have to add the following lines to your cursor-device

```

  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"

```

which limit the cursor to one screen.

However, the nvidia-settings-wizard for example maps both physical Panels to one Screen. So if you want to use these options, you will have to configure your Panels as two screens which is only possible by using the Xinerama option in your xorg.conf.

On my system this somehow disables the gnome-terminal (or any other terminal-application)...

---

### Post by hessiess on 2007-05-24
how can i get a volito2 working in ubuntu with no internet conection(internet only works in windows)

---

### Post by thedaemon on 2007-05-24
> **Amazing Iceman said:**
> Thanks for this HOWTO... My tablet now works great under 7.04!!!!

Just something I noticed:

- My Xorg.conf file was already configured for the tablet, but instead of pointing the device to /dev/input/wacom, it was pointing it to /dev/wacom.
- After installing wacom-tools and rebooting, still was pointing to /dev/wacom.

That was the only change I had to do manually to get it to work.
I also added the recommended setting to adjust sensitivity.

Maybe this is something that could be automated by the installation on the next release, to please the newcomers?


Thanks again.

--The Amazing Iceman


Awesome, got my tablet working! thanks

---

### Post by AlumaSqrl on 2007-05-24
> **sirarokh said:**
> I did find a solution for our problem:

You have to add the following lines to your cursor-device

```

  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"

```

which limit the cursor to one screen.

However, the nvidia-settings-wizard for example maps both physical Panels to one Screen. So if you want to use these options, you will have to configure your Panels as two screens which is only possible by using the Xinerama option in your xorg.conf.

On my system this somehow disables the gnome-terminal (or any other terminal-application)...


I've tried the Twinview and ScreenNo options with and without xinerama.  
They don't seem to have any effect on the problem in my case.  As the effectiveness of stable solutions seems to vary so widely, I'm beginning to suspect it might be something else... like the xorg video drivers for my geriatric Voodoo5.  I've sorted through - and updated - all the relevant wacom-related files and drivers i know about.  Either there's something else that controls how xorg handles events, or there's something interfering.

That's just my suspicion.

---

### Post by saxofoner on 2007-05-28
I'm having the same multiple monitor problems as you guys.  I've had it working in the past, you can find my thread, but now I'm nowhere.  I tried to do the "linux wacom" project thing, but I couldn't figure it out.

---

### Post by saxofoner on 2007-05-28
OKAY, I want some love for this one!  I managed to get it to map to one monitor perfectly, with the cursor and the paintbrush matching locations.  SCORE!!!!  
> Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "TwinView"      "horizontal"
  Option	"ScreenNo"	"0"
  Option        "TVResolution"  "1024x768,1024x768"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
  Option        "TwinView"      "horizontal"
  Option	"ScreenNo"	"0"
  Option        "TVResolution"  "1024x768,1024x768"
  
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"
EndSection

In Gimp I set it to "Screen", and my problems were solved.  The trick was that the "TVResolution" option was necessary, even though it shouldn't be.  Can someone tell me if it works for them?

---

### Post by AlumaSqrl on 2007-05-28
> **saxofoner said:**
> OKAY, I want some love for this one!  I managed to get it to map to one monitor perfectly, with the cursor and the paintbrush matching locations.  SCORE!!!!  

In Gimp I set it to "Screen", and my problems were solved.  The trick was that the "TVResolution" option was necessary, even though it shouldn't be.  Can someone tell me if it works for them?

I actually left my tablet elsewhere, so i can't test it yet.  
I'll let you know what shakes as soon as I get a chance, though.
Looking at "man wacom" now, I can't believe how many times I read right over that.  
... that, and i'm not sure of the behaviour with three screens.
we'll see.

---

### Post by saxofoner on 2007-05-28
yeah, I felt the same way when I found it.  I thought... well, it *shouldn't* need this, but who knows?  
Thanks for replying.

---

### Post by AlumaSqrl on 2007-05-29
> **saxofoner said:**
> yeah, I felt the same way when I found it.  I thought... well, it *shouldn't* need this, but who knows?  
Thanks for replying.

Well, I got my stuff back and I gave it all a whirl with the new outlook.
Sensible options might work for everyone else, but it doesn't do anything for me.  In fact, the ScreenNo, KeepShape, Twinview, and related TVResolution options don't do anything on my setup.  That's not to say that they don't fix the problem, but that they don't do ANYTHING AT ALL,  This dysfunctional behaviour persists even if i try running with only two monitors.  I tried to get it working dual-head first because nowhere is there clear documentation as to whether or not any of these options apply to server layouts with more than two defined screens.  

If i do the math with the pixel offsets in GIMP, it turns out that the brush is being mapped to an area equal to the sum of the active screen WIDTHS , but only Screen0's HEIGHT.  This is while the cursor is being mapped to both parameters of Screen0 only.  None of the wacom options actually have any effect, which leads me to believe that the xorg driver is somehow unable to function properly (as it's been replaced).   

It's also quite hard to keep fidgeting with the xorg config when X keeps exploding in my face every fifth restart.  This, i'm sure has something to do with video card drivers, as it locks my cards up and crashes the system hard after a while spewing garbled blinking vga text.  I think the next step is to pull all the cards and try some others with different drivers, just to see if it changes anything with the wacom driver.  I can't think of anything else, and this is just plain broken.

---

### Post by drummingpariah on 2007-05-30
I'm having a very hard time getting my ud-1212-r working.  Basically, I had to use a USB to 8pin serial adapter (not 9pin, this is the oldschool one that looks similar to s-video).  I think that could be the issue.  Rather than clutter up this thread with my nonsense testing that I've tried so far, I started a new one.  Has anyone else used a USB-Serial adapter?  It's a Keyspan usa 28x and seems to have been autodetected.  Any help that anybody can offer in getting this working would be greatly appreciated.

---

### Post by drummingpariah on 2007-05-31
My thread of what I've tried is in my sig.

---

### Post by Geta-Ve on 2007-06-05
My question (which there is a very likely chance it was answered) is if pressure sensitivity actually works in inkscape ( I don't think it does ) because if I used the calligraphy brush in IS it stays the same width all the time, where as in gimp it works perfectly.

Any ideas?

Thanks and apologies for the mundane.

---

### Post by AlumaSqrl on 2007-06-07
> **Geta-Ve said:**
> My question (which there is a very likely chance it was answered) is if pressure sensitivity actually works in inkscape ( I don't think it does ) because if I used the calligraphy brush in IS it stays the same width all the time, where as in gimp it works perfectly.



AFAIK, Inkscape uses a config dialog identical to that used by GIMP (under File-Input Devices).
as long as the appropriate pointer device is configured there in a manner identical to its configuration in GIMP, the behaviour should also be identical.  

Beyond that, I don't know.

---

### Post by KingCharles on 2007-06-07
I wish there were some extra gui features for the driver to be able to rotate the wacom tablet, like its windows counterpart. Sometimes is just plain useful ']

---

### Post by grisser on 2007-06-08
I've been holding back on posting as long as I could, thinking I could find solution through google and forum lurking, but I am at my wit's end.
I installed Ubuntu 6.1 and updated to Ubuntu 7.04 through update manager.
I read through every single thing regarding wacom on the net and nothing will make Gimp regonized my extended input (no extended input devices)

The tablet all work except pressure sensitivity.

My last attempt has been following direction from [https://help.ubuntu.com/community/WacomTabletIssue](https://help.ubuntu.com/community/WacomTabletIssue)
I am currently at step number 4. "Fix xinput or doodle time!"

while issuing the following command in terminal
```
grep -r "WACOM" *
```
inside the directory "/sys/bus/usb".  
The result is the follow
```

grep: warning: devices/2-1:1.0/ep_82/subsystem/usbdev2.4_ep00/device/net:wlan0/subsystem/eth0/device/bus/drivers/ata_piix/0000:00:1f.2/host2/scsi_host:host2/subsystem/host0/device/target0:0:0/0:0:0:0/block:sda/sda5/subsystem/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/ts1/device/bus/drivers/usb/usb3/ep_00/device: recursive directory loop

grep: warning: devices/2-1:1.0/ep_82/subsystem/usbdev2.4_ep00/device/net:wlan0/subsystem/eth0/device/bus/drivers/ata_piix/0000:00:1f.2/host2/scsi_host:host2/subsystem/host0/device/target0:0:0/0:0:0:0/block:sda/sda5/subsystem/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/ts1/device/bus/drivers/usb/usb3/ep_00/subsystem: recursive directory loop

grep: devices/2-1:1.0/ep_82/subsystem/usbdev2.4_ep00/device/net:wlan0/subsystem/eth0/device/bus/drivers/ata_piix/0000:00:1f.2/host2/scsi_host:host2/subsystem/host0/device/target0:0:0/0:0:0:0/block:sda/sda5/subsystem/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/ts1/device/bus/drivers/usb/usb3/ep_00/uevent: Permission denied

```
which repeats in loop until I close the terminal.

```
xsetpointer -l
```
returns
```

"pointer"       [XPointer]
"keyboard"      [XKeyboard]

```

Xorg.conf input device section is
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
	Option		"Device"		"/dev/input/mouse2"
# /dev/input/mouse2 was put in instead of mice following one of many directions.
#changing back to mice has no different effect.
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"Mode"		"relative"
	Option		"USB"		"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
EndSection

```

One thing I may have done to have cause the recursive directory loop is making this symbolic link.  Following the "In case this doesn't work" of [https://help.ubuntu.com/community/WacomTabletIssue](https://help.ubuntu.com/community/WacomTabletIssue) page

```
sudo ln -s /dev/input/event3 /dev/input/wacom
```

I had no idea now to undo it.  so in my infinite stupidity thinking that if I just issue command "sudo ln -s /dev/input/event3" it undo it somehow without not knowing exactly what "ln" even does.

help?

---

### Post by believe on 2007-06-15
hi,
i have a problem to get my voltio2 running... i installed wacom tools, set up my xorg.conf, but somehow the tablet is not mapped onto the whole screen. positioning and clicking works, but the cursor is like caged in a smaller area of the screen. 

the section from my xorg.conf:
[QUOTE="xorg.conf"]Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event5"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option "Mode" "Absolute"
  Option "KeepShape" "on"
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection[/QUOTE]


thanks for your help!

---

### Post by J-P on 2007-06-17
Hey, cheers for this, it worked, now ... the only thing I regret about dumping windows still remains Gimp, and it being vastly inferior to PS...  I will try to get as much out of it as I can though ;)

---

### Post by tofuwallaby on 2007-06-19
Hey Grisser - 
I had the same problem: tablet was moving the cursor, but GIMP wouldn't recognize it as an extended input device.

After much trial and error, it turns out it was because I was logging into GNOME with Xgl (so that I could use Beryl on my ATI card) and that was somehow blocking GIMP from seeing the tablet.

If you're using Xgl, try logging into GNOME without it -- on the login screen, choose change session -- and see if that helps.

---

### Post by webdr on 2007-06-20
For inverted scroll wheel/buttons on mouse of Intuos3.
In xorg.conf
Change the zaxismapping settings from "4 5" to "5 4"

---

### Post by drummingpariah on 2007-06-22
> **J-P said:**
> Hey, cheers for this, it worked, now ... the only thing I regret about dumping windows still remains Gimp, and it being vastly inferior to PS...  I will try to get as much out of it as I can though ;)

it isn't really a direct comparison.  I love 'em both!  They're tools, like a pencil and a pen.  Not quite the same, but you can get similar results (each has something it can do that the other can't).  Just offering my .02, don't anybody let this become a flame war.  If there's something you'd like to do in the GIMP that you can only do in PS, go ahead and start up a new thread and/or pm me.  I'd be happy to help out!

---

### Post by keithcausey on 2007-07-18
That's correct. There are three lines that needed changing after I installed the wacom-tools. The lines that I changed simply required running the code:
**sudo gedit /etc/X11/xorg.conf **
and then finding the three lines:
"/dev/wacom"
and changing them to:
"/dev/input/wacom"
After I did that, saved the file, and reset the computer the tablet range lay perfectly within my monitor's range! Best of luck - Keith

---

### Post by AlumaSqrl on 2007-07-21
> **KingCharles said:**
> I wish there were some extra features for the driver to be able to rotate the wacom tablet, like its windows counterpart. Sometimes is just plain useful ']

you can use xsetwacom to rotate the tablet in 90 degree increments, such as:

```
xsetwacom set stylus rotate 1 
```  

rotates the tablet CW 90 degrees.  I don't think this is very useful, as most people surely want a rotation ability that's more flexible and immediately useful than that.  xsetwacom does have quite a few options, though be wary of misleading and confusing documentation..

---

### Post by AlumaSqrl on 2007-07-21
In case anyone else was having issues with the improper mapping of multi-head layouts when using GIMP (cursor offset problems),  I decided to post the means by which I solved this on my computer.  I certainly cannot understand how exactly other people get this to work through simple edits of the config file, because I eventually had to resort to altering the xorg wacom driver.  Working back from the gdk cursor handling all the way to wcmCommon.c, the numbers are bogus for the axis across which the desktops span.  This is because the driver sums the widths of the screens whenever the absolute flag isn't set.  Simply setting 
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```
and commenting out the original assignment fixed this problem.  I haven't bothered looking into exactly WHY the math is being done like that, and I'm not entirely sure there isn't a particular reason for it.... but this method fixed the operation of the driver for my application and would serve as a solution for anybody else with a similar problem and a lack of patience.

---

### Post by tariqf on 2007-07-29
Cant get my wacom bamboo to work using the info in this thread nomatter what I try..

I have installed the latest wacom 0.7.8-2 which has bamboo support (and did the various settings in xorg.conf manually)..

Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......
Installed under /usr/local/bin


You need to compile and install wacom.(k)o manually if your kernel is out of date.


Now what? The problem seems to be that the device does not power up. It always flashes on for a second then goes off.

Tried Mandriva 2007 with newest driver and opensuse 10.2 and both power up (which is more than ubuntu does!) but does not work!

---

### Post by zgornel on 2007-07-30
Try doing a ```
sudo modprobe wacom
``` then restart X (ALT+CTRL+Backspace). And by the way, does anyone know is there is a way of using the tablet just after pluging it in (without having to restart the X server or start it with the tablet already plugged in)??It is really annoying.

---

### Post by samel on 2007-07-30
> Edit this below Section "InputDevice" under the "Configured Mouse".

Yes, but... which file? (I know, that's basic, but really new ones and I wonder this...)

---

### Post by natialos on 2007-08-09
> **samel said:**
> Yes, but... which file? (I know, that's basic, but really new ones and I wonder this...)

/etc/X11/xorg.conf

---

### Post by AlumaSqrl on 2007-08-14
> **zgornel said:**
> Try doing a ```
sudo modprobe wacom
``` then restart X (ALT+CTRL+Backspace). And by the way, does anyone know is there is a way of using the tablet just after pluging it in (without having to restart the X server or start it with the tablet already plugged in)??It is really annoying.

switch to a VT and back (crtl-alt-F1, ctrl-alt-F7)
after that, the xorg driver should regain control of the device
i found that out by accident, and it turns out that it's the method recommended on the linuxwacom site.

---

### Post by drummingpariah on 2007-08-17
> **AlumaSqrl said:**
> In case anyone else was having issues with the improper mapping of multi-head layouts when using GIMP (cursor offset problems),  I decided to post the means by which I solved this on my computer.  I certainly cannot understand how exactly other people get this to work through simple edits of the config file, because I eventually had to resort to altering the xorg wacom driver.  Working back from the gdk cursor handling all the way to wcmCommon.c, the numbers are bogus for the axis across which the desktops span.  This is because the driver sums the widths of the screens whenever the absolute flag isn't set.  Simply setting 
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```
and commenting out the original assignment fixed this problem.  I haven't bothered looking into exactly WHY the math is being done like that, and I'm not entirely sure there isn't a particular reason for it.... but this method fixed the operation of the driver for my application and would serve as a solution for anybody else with a similar problem and a lack of patience.

Actually, I am.  I haven't had a chance to mess with it, and have actually been considering assigning all input to ONE screen (the larger of the two, which is the one I do all my art on).  I'd also like to be able to assign it to JUST gimp/inkscape/etc and not to X as a cursor.  I know it's been mentioned, but I've been having a horrible time finding out how to do it.  Here's my current information from xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1680 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/ttyUSB1"
    Option         "Type" "stylus"
    Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/ttyUSB1" 
    Option         "Type" "eraser"
    Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/ttyUSB1"
    Option         "Type" "cursor"
    Option        "PressCurve" "0,0,100,100"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CMO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```


I'm off to work, but if anybody has any input or suggestions on a decent way to map the input properly (right now the left side of the tablet goes to the right screen, and the right side goes to the left screen) or just to limit it to certain apps, it'd be much appreciated.

---

### Post by drummingpariah on 2007-08-18
> **AlumaSqrl said:**
> 
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```

I'm convinced that this is the only solution that will work.  I tried the TVResolution, Twinview, ScreenNo settings on every possible configuration, and no love from GIMP.  My screens are still backwards (only to the tablet, the mouse has them mapped correctly), and GIMP is still using both monitors' combined resolution as the mapped area.  I made that change, but what's next?  Do I need to recompile the driver, or just reload the module, or is something else required?  More importantly, what do I do for whatever's required?  

Just for the record, I'm good at following directions, but reworking drivers is totally new to me.  I'd appreciate any information you can point me to (as I understand not everybody enjoys writing howto's on their free time :)).

Thanks for the lead on this, I'm going to finish eating up my weekend trying to figure it out on my own.

---

### Post by drummingpariah on 2007-08-18
The driver quits on:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no:cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... ychecking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel sources... /lib/modules/2.6.20-16-generic/build
checking for kernel module support... yes
checking for kernel module versioning... yes
checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg and /usr/xc/include
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for stack-protector flags support in gcc... yes
checking for X lib directory... found
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... /usr/include/tcl8.4/
checking for tk header files... found
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for specifying Wacom X driver module path... ***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} 
*** without Xorg SDK or XFree86 build environment
*** wacom_drv.o will not be built
***
checking if gcc accepts -fno-merge-constants... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.19
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.20-16-generic/build
           Xorg SDK - no /usr
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

:  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
----------------------------------------

```

which corresponds with the Linux Wacom Project information provided on [Compiling]("http://linuxwacom.sourceforge.net/index.php/howto/config") that the following is the cause of the problem:
```
checking for specifying Wacom X driver module path... ***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} 
*** without Xorg SDK or XFree86 build environment
*** wacom_drv.o will not be built
***
```

but what do I specify for the driver module path?

---

### Post by cosmicflicker on 2007-08-28
hi! i'm new here, and i have the same problem as Geta-Ve up on the 21. page. So, my pressure sensitivity works in Gimp, and not in Inkscape, although they have been configured in the same fashion.
i use ubuntu feisty and wacom volito.
any help?

---

### Post by zgornel on 2007-08-29
> **drummingpariah said:**
> The driver quits on:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no:cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... ychecking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel sources... /lib/modules/2.6.20-16-generic/build
checking for kernel module support... yes
checking for kernel module versioning... yes
checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg and /usr/xc/include
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for stack-protector flags support in gcc... yes
checking for X lib directory... found
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... /usr/include/tcl8.4/
checking for tk header files... found
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for specifying Wacom X driver module path... ***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} 
*** without Xorg SDK or XFree86 build environment
*** wacom_drv.o will not be built
***
checking if gcc accepts -fno-merge-constants... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.19
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.20-16-generic/build
           Xorg SDK - no /usr
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

:  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
----------------------------------------

```

which corresponds with the Linux Wacom Project information provided on [Compiling]("http://linuxwacom.sourceforge.net/index.php/howto/config") that the following is the cause of the problem:
```
checking for specifying Wacom X driver module path... ***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} 
*** without Xorg SDK or XFree86 build environment
*** wacom_drv.o will not be built
***
```

but what do I specify for the driver module path?

Try specifying ```
--with-x-src=/path/to/xfree86/source
```. You could also try to install the development files for xorg and retry configure.

---

### Post by whatisdot on 2007-09-04
Ok, heres a problem.  I have installed-reinstalled-completely removed and installed several times, and now I can't use xidump or wacdump:
```
wacdump: error while loading shared libraries: 
libtinfo.so.5: cannot open shared object file: 
No such file or directory
```
I have the wacom-tools installed, so I don't know what the deal is...

---

### Post by dsmithhfx on 2007-09-05
I finally got my Graphire 4 working in Feisty -- as a mouse substitute (absolutely necessary for me since I have CTS).

Here are my xorg.conf relevant bits:

> Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option	"PressCurve"	"50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
EndSection

#adding InputDevice "pad" causes boot failure in this section

Thanks for the, at times, confusing and conflicting theories, instructions etc. It seems we are left to trial and error, perhaps because of idiosyncratic interactions between motherboard, devices and drivers. Anyway, with your help, I did it, and good luck and keep trying for those who haven't. I took me ~8-10 hours total, on a half dozen sessions stretching over two months, and the purchase of a new tablet (gave up on an old serial tablet) to get to this point....

---

### Post by StrixVarius on 2007-09-05
First - Thanks! Fabulous howto, got my tablet working a lot more than it ever has before.

Second - Wanted to point out some problems I'm having, see if anybody else has the same issues, maybe find a way to fix them:

1. If I unplug the USB cable then plug it back in, the tablet will still left and right click but will not move the cursor.

2. The scroll wheel direction is inverted

3. I appreciate the option allowing for pressure sensitivity changes, but how about mouse (cursor) speed/acceleration tweaking?

Thanks!

Hunter

---

### Post by whatisdot on 2007-09-05
StrixVarius,

I also have this problem.  I found that my curser movement is hit or miss, but when I put the line:

Option    "Button1"  "1"

in  the "curser" section, it works when I take the mouse off of the pad and place it back on after initial boot.  As far as the inverted mouse problem, the quick fix is this in the terminal:

```
xsetwacom set cursor RelWUp "button 5"
xsetwacom set cursor RelWDn "button 4"
```

I don't know how to set this in the xorg.conf file, because they don't explain it very well in the documentation on the linuxwacom website, and few people address this.  In fact, it would be nice if someone would test the functionallity of each of the "options" in "man wacom."  I was planning on doing this myself and posting the results here, but because I can't use xsetwacom or wacdump (as stated previously) I can't quite do this.  Anyone else?

---

### Post by evissecx on 2007-09-06
Ok, now I've finally got the wacom mapped to one of my screens.
But the problem now is that gimp doesn't co-op with the wacom.
The cursor is offset from the pen pointer.
Is there a way to fix this. if not, the mapping is rather useless :S

Thanks in advance :)

Edit: I've red about the text string:
> totalWidth = screenInfo.screens[priv->currentScreen]->width;
But i don't know where to put this. I don't really understand everything you guys talk about now.
Is it something I will add when compiling the drivers?
Sorry for my bad english.

---

### Post by drummingpariah on 2007-09-09
> **evissecx said:**
> Ok, now I've finally got the wacom mapped to one of my screens.
But the problem now is that gimp doesn't co-op with the wacom.
The cursor is offset from the pen pointer.
Is there a way to fix this. if not, the mapping is rather useless :S

Thanks in advance :)

Edit: I've red about the text string:

But i don't know where to put this. I don't really understand everything you guys talk about now.
Is it something I will add when compiling the drivers?
Sorry for my bad english.

It's a line you modify when compiling the drivers.  As far as I can tell, the wacom driver should have that line instead of the convoluted line that's currently in there.  You might also be able to work around it by mapping the input to just GIMP instead of the whole screen if you aren't comfortable with compiling drivers.

---

### Post by william_nbg on 2007-09-11
I seem to be having the same problem a few others had in this thread, but haven't found a solution yet.

I've just bought a 'Wacom Volito 2' which pretty much worked out of the box - as far as just moving the cursor around the screen. But it doesn't show up in the input devices in Gimp or Inkscape.

Does anyone have any ideas what I could try??? 

Without pressure sen. it's not much better than a mouse.

---

### Post by william_nbg on 2007-09-11
After a little looking around I have found out a few things:

The pad works OK in the 'wacdump' test

But doesn't even show up in xidump

????

---

### Post by william_nbg on 2007-09-11
Another thing I've noticed is: I can take the device completely out of 'xorg.conf' 

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "PressCurve"    "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option  


Which I put in there myself anyway - after removing, restarting X, the pad works just as it had. OK, but can't set it up in Gimp. So the driver seems to work, it show up, but X doesn't recognize it at all??

---

### Post by william_nbg on 2007-09-12
Got it - oh yeah!!

For some reason when I first plugged the pad in, installed Wacom tools, it didn't write it into my xorg.conf as it should have. I later wrote it in myself - which doesn't really work.

So after sleeping on it - often a good idea. I just ran:

sudo dpkg-reconfigure xserver-xorg

and presto! it was all written into the xorg.conf and X see it - meaning Gimp too.

Now I'm off and drawing.

Hope this helps, if anybody else has the same hang-up.

---

### Post by greglaun on 2007-09-13
I have a thinkpad x60 tablet that used to work.  I reinstalled Feisty and now the pen sends button events when it's about an inch away from the screen, making it pretty much useless for drawing and anything else.

I tried compiling newer drivers, editing several lines in xorg.conf as suggested by this thread, and several other things.  It behaves exactly the same way on Gentoo as it does on Feisty.  I also tried Dapper and Gutsy and both do the same thing.

I just had the screen replaced, is it possible that this is a hardware problem?  Does anyone have similar problems?  Thanks!

---

### Post by mgrenier on 2007-09-21
Please help.

I have a wacom intuos3 tablet. running the latest version on ubuntu.

I've followed all the instructions about setup that I can find.

After a reboot sometimes the tablet works, and sometimes it does not.

I've included my xorg.conf file if that helps

---

### Post by william_nbg on 2007-09-22
> Please help.

I have a wacom intuos3 tablet. running the latest version on ubuntu.

I've followed all the instructions about setup that I can find.

After a reboot sometimes the tablet works, and sometimes it does not.

I've included my xorg.conf file if that helps



Are you running the tablet over some kind of usb bus? I had that problem before and when I changed it to a usb port it worked fine.

---

### Post by mgrenier on 2007-09-24
Thanks for the reply.  I'm plugged right into my computer.  But I do have a USB bus which I  have a  printer plugged into.

---

### Post by kolyma on 2007-10-21
> I have a wacom intuos3 tablet. running the latest version on ubuntu.

I've followed all the instructions about setup that I can find.

After a reboot sometimes the tablet works, and sometimes it does not.

mgrenier, I have the same problem. Intuos3, Feisty up-to-date, plugged directly into the USB port, and my xorg.conf looks similar to yours (attached), although without the TabletPC stuff. Every time I start my computer, it's a crapshoot whether the tablet works or not. When it works, it works perfectly. When it doesn't, the light on the tablet responds to stylus inputs, but nothing happens on the screen.

I can't find reference to this problem in any forum posts.

Can anyone help?

---

### Post by ebullient on 2007-10-26
Anyone fix the proportion or ratio of the tablet as related to the screen?  In windows the drivers have an option to force proportion to the screen, it may use a little less of the tablet but your movements translate to more accurate results.  Anyway, I'm trying to run this on a widescreen monitor and the horizontal is way more sensitive than the vertical.  I'll get used to it I guess, but it would be nice if they behaved the same.

---

### Post by mukiex on 2007-10-29
Usability concerns :

1. (offtopic but just came up) The quick reply system is (bad word)ing broken. Never mind the trouble spent looking for a reply link, why not just let people type in the message box? WhyTF is the message box even here if it doesn't works unless you click reply? Seriously.

2. For F(anger)'S SAKE. The Graphire 4 pad's mouse still scrolls f(more anger)ing backwards. The Linux-Wacom project had this bug stomped in FEBRUARY. That was **two Ubuntu releases ago**. And why isn't the wacom stuff enabled in xorg.conf from default?! All this talk about not having to edit text files in Gutsy, and look WTF you have to do to get a tablet working. Does Xorg **explode** if you don't have a tablet plugged in but enabled the data in the conf file?! Wacom-Tools is a ******* 50 kilobyte package. There's ZERO reason why it shouldn't be installed by default.

I apologize for the language, but it's agrivating knowing a simple problem with a simple solution has gone a **year** without a fix. I can only dream that the next version, the one with LTS, has this thing nipped.

---

### Post by kickstart_in_FR on 2007-11-10
Hello there, I have already searched the forums for a solution to my problem, but I couldn't find any relevant threads, so I thought it might be the best idea to just post it here.

I have a Graphire2, which works just fine in Feisty, except the mouse does behave just like the pen, which means it is set to the absolute movement. I can't get the mouse to work in relative movement, so the mouse is just not usable.
Normally I wouldn't care, but I can't play any of 3D games with the pen, it is only possible with the mouse set to relative movement. I don't want to buy an extra mouse just for playing those games, if I have to, I will, but first I wanted to ask you what is wrong with my configuration.

As already said, I use Feisty with all the latest updates and the relevant parts of my xorg.conf look like this:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"TouchpadOff"		"2"
	Option		"MaxTapTime"		"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"KeepShape"	"1"
	Option		"Mode"	"Absolute"
	Option          "USB"                   "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"KeepShape"	"1"
	Option		"Mode"	"Absolute"
	Option          "USB"                   "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"Mode"	"Relative"
	Option          "USB"   "on"
	Option 		"Speed" "1.5"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

I don't know whats wrong or if it is just a bug that isn't solved, I hope you can help me. Thanks in advance.

---

### Post by nemesis8601 on 2007-11-30
Hi,

I just got a Wacom Bamboo, and after following all the steps in the guide, my computer still won't recognize it. The lights on the tablet light up, but it won't respond. Also, when I launch GIMP or Inkscape it says no external devices were found. 

I also installed wacom-kernel-source and xserver-xorg-input-wacom in addition to wacom-tools.

Here is my xorg file. Thanks!

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dvorak"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/event1"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/event1"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/event1"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"DELL E228WFP"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL E228WFP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1680x1050@75"	"1600x1024@60"	"1920x1200@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by drummingpariah on 2007-12-01
> **mukiex said:**
> Does Xorg **explode** if you don't have a tablet plugged in but enabled the data in the conf file?! Wacom-Tools is a ******* 50 kilobyte package. There's ZERO reason why it shouldn't be installed by default.

I apologize for the language, but it's agrivating knowing a simple problem with a simple solution has gone a **year** without a fix. I can only dream that the next version, the one with LTS, has this thing nipped.

There are lots (and lots and lots) of 50kb packages that cults of users (much like ourselves) would expect to be installed by default, but those packages really add up quickly.  I'm with you as far as frustration goes, since Keyspan compatibility was removed in Gutsy, I can't use my tablet at all.  The real kicker is trying to find the module that needs to be compiled, and it's just been a world of (unnecessary) hassle.

Anyway, venting doesn't accomplish a whole lot.  If you do gain any ground, please please PLEASE document it.  All the information we can possibly confirm is going to be in the right direction, and isn't that the whole idea behind Ubuntu?  People helping people?

On that note, I don't see any glaring problems with the two latest xorg.conf files.  It's possible that the xorg.conf isn't the problem, and it's actually an issue with the driver/kernel.  What version of the driver, and what dist of Ubuntu (edgy, feisty, gutsy, etc) are you running?

---

### Post by nemesis8601 on 2007-12-03
How do you know what event to put instead of "wacom"  for "dev/input/wacom"? I read on a previous post that those lines had to be changed. For example, some people changed it to "dev/input/event2" but I'm not sure why they put event 2 instead of something else. Can anyone help? That may be the problem I'm having.

---

### Post by gertvdijk on 2007-12-03
Great that Wacom tablets are supported in Linux, but I have one, 18 months old, but I can't find anything about it regarding Linux support! :confused:
My model is de Graphire BT (Bluetooth, CTE-630BT). It is being identified as a standard HID input device in Windows and a Wacom service is running for the features and absolute positioning for the pen.
Does anybody have a Graphine BT or Wireless Pen Tablet (same thing, but new model no)? Or can anyone give me any hints about how to get it to work?
Any help appreciated. :)

---

### Post by drummingpariah on 2007-12-07
> **gertvdijk said:**
> Great that Wacom tablets are supported in Linux, but I have one, 18 months old, but I can't find anything about it regarding Linux support! :confused:
My model is de Graphire BT (Bluetooth, CTE-630BT). It is being identified as a standard HID input device in Windows and a Wacom service is running for the features and absolute positioning for the pen.
Does anybody have a Graphine BT or Wireless Pen Tablet (same thing, but new model no)? Or can anyone give me any hints about how to get it to work?
Any help appreciated. :)

I'm not sure if it's officially supported or not, but if it's not we can probably fix that.  What is your wacdump output and where is the input from the tablet going?

> **nemesis8601 said:**
> How do you know what event to put instead of "wacom"  for "dev/input/wacom"? I read on a previous post that those lines had to be changed. For example, some people changed it to "dev/input/event2" but I'm not sure why they put event 2 instead of something else. Can anyone help? That may be the problem I'm having.

Depending on your driver and how you're mapping the input, it may just be /dev/input/wacom (by default) or something screwy, like what I'm doing (/dev/ttyUSB0 because I have a serial->usb converter).  Check the documentation (man docs especially) and it should tell you specifically what to use for your model.

I'm still having a problem with cursor offset in GIMP when using two screens.  I'm fairly sure that it's not a driver problem, but instead a "relative" or "absolute" positioning problem.  I've recompiled the driver with totalWidth reconfigured, as mentioned earlier (I'll quote it if I remember to look again) but is anybody else running into this same problem?  It seems to be **less** of a problem if I set "stylus" and "cursor" to different map values in GIMP (such as screen/window).  More on that later, but has anybody solved this elusive issue?

---

### Post by caelcynndarr on 2008-01-02
worked awesome Thanks

---

### Post by june.itech on 2008-01-13
Thank you very much for this!

---

### Post by yitzle on 2008-01-14
When I add the line(s) to the ServerLayout section, gdm crashes when I log in.
```
Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
#       Option          "PressCurve"    "50,0,100,50"
#       Option          "Mode"          "relative"
EndSection
Section "ServerLayout"
        InputDevice     "stylus"        "SendCoreEvents"
```
```
/dev/input
crw-rw---- 1 root root 13,  64 2008-01-13 19:07 event0
crw-rw---- 1 root root 13,  65 2008-01-13 19:07 event1
crw-rw---- 1 root root 13,  66 2008-01-13 19:07 event2
crw-rw---- 1 root root 13,  67 2008-01-13 19:07 event3
crw-rw---- 1 root root 13,  63 2008-01-13 19:06 mice
crw-rw---- 1 root root 13,  32 2008-01-13 19:07 mouse0
crw-rw---- 1 root root 13,  33 2008-01-13 19:07 mouse1
lrwxrwxrwx 1 root root       6 2008-01-13 19:07 tablet-graphire3 -> event2
lrwxrwxrwx 1 root root       6 2008-01-13 19:07 wacom -> event2

```

---

### Post by patchido on 2008-02-02
i followed this and all it did was damage my xorg file... i had to use 

sudo dpkg-reconfigure -phigh xserver-xorg

so i could run xorg again.... i have a intuos3 and would like for it to work.. how does my xorg need to look??

oo btw when i used yum it told me an error.. that i was missing a package.. but i installed it and still told me the same

---

### Post by yitzle on 2008-02-02
Making a dated backup before playing around with files is always smart...

---

### Post by the lah on 2008-02-03
Great HOWTO, Everything worked out great on my Wacom Graphire 2! :)

---

### Post by drummingpariah on 2008-02-06
> **patchido said:**
> i followed this and all it did was damage my xorg file... i had to use 

sudo dpkg-reconfigure -phigh xserver-xorg

so i could run xorg again.... i have a intuos3 and would like for it to work.. how does my xorg need to look??

oo btw when i used yum it told me an error.. that i was missing a package.. but i installed it and still told me the same

well, what package?  What does your xorg.conf look like before modifying it?  Give us information to work with, and we'll be happy to help.

---

### Post by Robynsveil on 2008-02-10
I've noticed a few people add their issues with wacom Bamboo, and so I thought I might too. I must say, first off, that this is a great forum with a keen group of people, keen on making their computers do what they want it to, as opposed to having some company make that decision for them... and stimulates grey matter in the process.

I've had a few trials getting my USB wacom Bamboo to work so far: must have re-compiled the drivers and stuff eight or nine times until I figured out what the problem was. In the process, I have become on intimate terms with /etc/X11/xorg.conf, tweaking this and that until I've finally gotten not only the tablet essentially working, but have removed some redundant entries as well.

The instructions to get a set of drivers working so that your Bamboo will show up I found here:
[http://ubuntuforums.org/showthread.php?t=631881]("http://ubuntuforums.org/showthread.php?t=631881")

The last issue I have is with a cursor/draw-point offset in The GIMP. That is, my cursor is down and to the right of where my brush is, which makes drawing awkward if not impossible. BTW, I've got stylus, cursor and eraser set to 'screen', as per recommendation.

I've carefully read through this thread and there seem to be two schools of thought on how to best address this.
Saxofoner suggested:
> OKAY, I want some love for this one! I managed to get it to map to one monitor perfectly, with the cursor and the paintbrush matching locations. SCORE!!!!
Quote:
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom" #USB ONLY
Option "Type" "stylus"
Option "USB" "on" #USB ONLY
Option "TwinView" "horizontal"
Option "ScreenNo" "0"
Option "TVResolution" "1024x768,1024x768"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom" #USB ONLY
Option "Type" "eraser"
Option "USB" "on" #USB ONLY
Option "TwinView" "horizontal"
Option "ScreenNo" "0"
Option "TVResolution" "1024x768,1024x768"

EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom" #USB ONLY
Option "Type" "cursor"
Option "Mode" "relative"
Option "USB" "on" #USB ONLY
Option "Twinview" "horizontal"
Option "ScreenNo" "0"
EndSection
In Gimp I set it to "Screen", and my problems were solved. The trick was that the "TVResolution" option was necessary, even though it shouldn't be. Can someone tell me if it works for them?


whilst AlumaSqrl was pretty sure that:
> In case anyone else was having issues with the improper mapping of multi-head layouts when using GIMP (cursor offset problems), I decided to post the means by which I solved this on my computer. I certainly cannot understand how exactly other people get this to work through simple edits of the config file, because I eventually had to resort to altering the xorg wacom driver. Working back from the gdk cursor handling all the way to wcmCommon.c, the numbers are bogus for the axis across which the desktops span. This is because the driver sums the widths of the screens whenever the absolute flag isn't set. Simply setting
Code:

totalWidth = screenInfo.screens[priv->currentScreen]->width;

and commenting out the original assignment fixed this problem. I haven't bothered looking into exactly WHY the math is being done like that, and I'm not entirely sure there isn't a particular reason for it.... but this method fixed the operation of the driver for my application and would serve as a solution for anybody else with a similar problem and a lack of patience.

was going to be the only way to go. I'm not above rebuilding (compiling) a .c file if that will fix it, but might need a bit of hand-holding... anyone willing to give some pointers, or has someone arrived at another, more definitive solution?

---

### Post by Robynsveil on 2008-02-10
> **saxofoner said:**
> OKAY, I want some love for this one!  I managed to get it to map to one monitor perfectly, with the cursor and the paintbrush matching locations.  SCORE!!!!  


In Gimp I set it to "Screen", and my problems were solved.  The trick was that the "TVResolution" option was necessary, even though it shouldn't be.  Can someone tell me if it works for them?

Sorry to say, Saxofoner, I did try it and it didn't work for me. I actually even set my monitor resolution to 1024 x 768 (which is almost as bad as 640 x 480 is now) and my xorg.conf was like:
> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
	Option		"Mode"		"Absolute"
        Option		"PressCurve"	"50,0,100,50"
	Option		"ScreenNo"	"0"
	Option		"TVResolution"	"1024x768,1024x768"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"Mode"		"Absolute"
	Option		"USB"		"on"
	Option		"ScreenNo"	"0"
	Option		"TVResolution"	"1024x768,1024x768"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"CM753"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"CM753"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1280" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

...but the offset was as bad as ever... no change at all. Thinking of barking up the altering-the-xorg-wacom-driver tree.

---

### Post by Robynsveil on 2008-02-10
> **AlumaSqrl said:**
> In case anyone else was having issues with the improper mapping of multi-head layouts when using GIMP (cursor offset problems),  I decided to post the means by which I solved this on my computer.  I certainly cannot understand how exactly other people get this to work through simple edits of the config file, because I eventually had to resort to altering the xorg wacom driver.  Working back from the gdk cursor handling all the way to wcmCommon.c, the numbers are bogus for the axis across which the desktops span.  This is because the driver sums the widths of the screens whenever the absolute flag isn't set.  Simply setting 
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```
and commenting out the original assignment fixed this problem.  I haven't bothered looking into exactly WHY the math is being done like that, and I'm not entirely sure there isn't a particular reason for it.... but this method fixed the operation of the driver for my application and would serve as a solution for anybody else with a similar problem and a lack of patience.

I've found wcmCommon.c and brought it up in Bluefish. Although I program a bit, I've never been able to get my head around c. There appear to be a fair few references to Totalwidth = ... do we comment out and replace with "screenInfo.screens[priv->currentScreen]->width" all instances? or is there a particular line number I need to be at? or in a specific function?
Once I've made this change, do I just re-issue a ./configure ... make ... sudo make install as before? Please excuse the noob questions... a lot of people seem to be asking the same questions not only on this board but also on the GIMPTalk board, so it would be nice to maybe create a HOWTO for utter noobs to be able to follow, along the lines of the one at the beginning of this thread. Seems a pity to have the bloody thing working finally and yet still have this cursor/draw-point offset issue plaguing so many.

---

### Post by megadeus on 2008-02-12
Okay, this one might have been brought up, but my searching was not able to find it:

I'm using a Graphire 2 and through xsetwacom and editing xorg.conf I've managed to get the tablet mostly working. 

The problems:

(1) The tablet registers a "click" whenever the tip gets within sensing range of the tablet. Normally, this would be the area you'd hover in if you wanted to move the cursor onscreen without actually drawing (or clicking and dragging or whatever). This can be solved with TPCButton set to 1, but it doesn't solve the next problem.

(2) Whenever the tablet registers a "click" (either by hovering when TPCButton is set to 0 or when the tip touches the tablet when TPCButton is 1) the action is that of a right-click, not a left-click. I've tried changing Button1 to various values with xsetwacom, but none have remedied the right-click problem.

I can work with the latter problem, but it is REALLY annoying sometimes, so I'm hoping for a good solution. Any advice?

---

### Post by Robynsveil on 2008-02-12
> **AlumaSqrl said:**
> In case anyone else was having issues with the improper mapping of multi-head layouts when using GIMP (cursor offset problems),  I decided to post the means by which I solved this on my computer.  I certainly cannot understand how exactly other people get this to work through simple edits of the config file, because I eventually had to resort to altering the xorg wacom driver.  Working back from the gdk cursor handling all the way to wcmCommon.c, the numbers are bogus for the axis across which the desktops span.  This is because the driver sums the widths of the screens whenever the absolute flag isn't set.  Simply setting 
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```
and commenting out the original assignment fixed this problem.  I haven't bothered looking into exactly WHY the math is being done like that, and I'm not entirely sure there isn't a particular reason for it.... but this method fixed the operation of the driver for my application and would serve as a solution for anybody else with a similar problem and a lack of patience.

Impatient cow that I am, I'm going to have a go at fixing this myself. The above post left me with a few questions that perhaps another guru might be able to answer for me. First off:
> numbers are bogus for the axis across which the desktops span
By that would be meant those x, y coordinates that define, what, screen size in pixels? Like in that comment in wcmCommon.c for the xf86WcmSetScreen function:
> /******************************************
 * xf86WcmSetScreen --
 *   set to the proper screen according to the converted (x,y).
 *   this only supports for horizontal setup now.
 *   need to know screen's origin (x,y) to support 
 *   combined horizontal and vertical setups
 *************************************************/

Converted *where*?
Somehow I think AlumaSqrl's issue and the developer's note are related. 

Anyway, I brought up wcmCommon.c in Bluefish, and went to the xf86WcmSetScreen function in the static functions group. I found a reference to that totalWidth = statement, which seems to be one of those weird (to me) situations where the variable takes on its original value [COLOR="Red"]**plus**[/COLOR] what's after the equal sign (which I understand means assignment, as in: var1 = var2 means var1 takes on the value of var2). I commented it out and replaced it with Aluma's code... like so:
```
/*... An effort of resolve the cursor-drawpoint offset...
	   from AlumaSqrl in Ubuntuforum post:
	
			totalWidth += screenInfo.screens[i]->width;
...*/
			totalWidth = screenInfo.screens[priv->currentScreen]->width;
/*... end mod  ...*/

```

There aren't many more references to this variable. This one I left alone...:

```
	if (priv->screen_no == -1)
	{
		for (i = 0; i < priv->numScreen; i++)
		{
			**[COLOR="Red"]totalWidth += screenInfo.screens[i]->width;[/COLOR]**
			if (maxHeight < screenInfo.screens[i]->height)
				maxHeight = screenInfo.screens[i]->height;
		}
		for (i = 0; i < priv->numScreen; i++)
		{
			if (v0 * totalWidth <= (leftPadding + 
				screenInfo.screens[i]->width) * sizeX)
			{
				screenToSet = i;
				break;
			}
			leftPadding += screenInfo.screens[i]->width;
		}
	}
	else 

```
Not sure if this also needs to be modified.
Thanks to all who reply...

---

### Post by Robynsveil on 2008-02-12
> **drummingpariah said:**
> I'm not sure if it's officially supported or not, but if it's not we can probably fix that.  What is your wacdump output and where is the input from the tablet going?



Depending on your driver and how you're mapping the input, it may just be /dev/input/wacom (by default) or something screwy, like what I'm doing (/dev/ttyUSB0 because I have a serial->usb converter).  Check the documentation (man docs especially) and it should tell you specifically what to use for your model.

I'm still having a problem with cursor offset in GIMP when using two screens.  I'm fairly sure that it's not a driver problem, but instead a "relative" or "absolute" positioning problem.  I've recompiled the driver with totalWidth reconfigured, as mentioned earlier (I'll quote it if I remember to look again) but is anybody else running into this same problem?  It seems to be **less** of a problem if I set "stylus" and "cursor" to different map values in GIMP (such as screen/window).  More on that later, but has anybody solved this elusive issue?

I'm still working on this as well. Quick question: did you change both references of:
```
totalWidth += screenInfo.screens[i]->width;
```
to
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```

Almost wondering whether that plus sign needs to be there... as in:

```
totalWidth **[COLOR="Red"]+=[/COLOR]** screenInfo.screens[priv->currentScreen]->width;
```

Not sure if that makes sense, since I can't really figure out what this code is trying to do, exactly. The statement occurs in a 'for' loop, where the 'i' variable value is incremented while its value is less than that of priv->numScreen... and I can't find where priv->numScreen is initialized. Maybe in the calling program...

---

### Post by fenrisswolf on 2008-02-18
Thanks for the how to!

Just one quick note to noobs (like me!)  when using a serial tablet, and editing the xorg file, make sure your **/dev/ttyS0** line includes that capital "S." 

I was having the hardest time setting up my tablet until I noticed that typo! :lolflag:

---

### Post by cipher_nemo on 2008-03-02
Thank you everyone for helping with this! I currently use WinXP for working with Photoshop, etc., and am looking into getting a Cintiq 12WX or other Wacom tablet. It's good to know that there is hope for using it in GIMP with pressure sensitivity.

I prefer Photoshop (just because I'm use to it), but I don't mind GIMP if I get a little more comfortable with it. This will help make my eventual transition to exclusively use Ubuntu as my main desktop.

Thanks again everyone! :D

---

### Post by markhammill on 2008-03-02
> **FrankL said:**
> I got a Toshiba Tecra M7 tablet PC and the pen is actually working, thanks to this howto. Thanks!

But I also want the button on my pen to do something. I would like it to work as a right mouse button. Now it just doesn't have any real function.

Any idea how I can activate it? Thanks in advance!

Hi FrankL,

I also have a Tecra M7 running Gutsy Gibbon but I haven't managed to get the stylus to work at all yet. 

Could you tell me how to do it. Each time I try I can't boot the log in screen for some reason. 

I have the intel graphics rather then the nvidia one if this makes a difference. 

Have you got your headphones without the speakers, bluetooth, figure print reader or any of the other buttons working that you could help me on. 

Thanks in advance.

---

### Post by KaiserM on 2008-03-06
Does anyone have the Xorg for the CTE-630 BT to get the pad buttons working?

This isn't correct:

> Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"pad"
        Option          "ButtonsOnly" "on"
        Option          "Button9" "2"
        Option          "Button13" "3"
        Option          "ForceDevice"   "ISDV4" # Tablet PC ONLY
        Option          "USB"   "on"
        Option          "TVResolution" "1024x768,1024x768"
        Option          "ScreenNo"     "0"
        Option          "Twinview"      "horizontal"
EndSection

As you can see; I've tried near everything; at the moment I have pressure sensitivity working, just 2 bugs really.

When I power the tablet off and then back on, it gets all uncalibrated and functions hyperactively.

The two pad top buttons uh...don't work.

Any help would be appreciated.

Edit: I just changed dev/input/wacom to dev/input/event10; it didn't fix my buttons either

---

### Post by waggingwabbit on 2008-04-18
how do you guys find out about all those options you can input for the tablet?

---

### Post by ERICwithanH on 2008-06-02
Here: [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

My Wacom Intuos3 tablet works, but I'm having a a couple of problems.  Some mouse clicks register, some don't -- it's super annoying.  Also, the cursor moves two pixels at a time, rather than one, which sucks when I'm in Photoshop trying to do super precise work.  When I use my pen, the cursor behaves exactly as it should; the cursor moves one pixel at a time and every click registers.

Does anyone have any advice they could give me?

I'm running Ubuntu 8.04 Hardy.

I tried multiple values for the Supress option and had little success.

Here's my xorg.conf file:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	Option "TwinView"
	Option "MetaModes" "1680x1050 1680x1050"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"
        InputDevice    "pad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "stylus"
	Option        "USB"           "on"
	Option        "PressCurve"    "50,0,100,50"

	Option        "KeepShape"     "on"
	Option 	      "Suppress"      "0"
	Option	      "Twinview"      "horizontal"
	Option        "ScreenNo"      "0"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "eraser"
	Option        "USB"           "on"

	Option        "KeepShape"     "on"
	Option	      "Twinview"      "horizontal"
	Option        "ScreenNo"      "0"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "cursor"
	Option        "Mode"          "relative"
	Option        "USB"           "on"

	Option        "Speed"         "2"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "pad"
	Option        "Device"        "/dev/input/wacom"
	Option        "Type"          "pad"
	Option        "USB"           "on"
EndSection


```

---

### Post by baylessiii on 2008-06-19
Hello. I'm completely new to Ubuntu, a professional artist who desperately wants to get this tablet working. I'm cringing as I ask this because I know it's probably simple: Where do I input that code you suggested? How do I get to a screen that accepts those lines you provided? Thank you so much in advance and I hope I made some sort of sense.

---

### Post by xdarkday on 2008-06-19
> **baylessiii said:**
> Hello. I'm completely new to Ubuntu, a professional artist who desperately wants to get this tablet working. I'm cringing as I ask this because I know it's probably simple: Where do I input that code you suggested? How do I get to a screen that accepts those lines you provided? Thank you so much in advance and I hope I made some sort of sense.

open terminal
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by baylessiii on 2008-06-19
> **xdarkday said:**
> open terminal
```
sudo gedit /etc/X11/xorg.conf
```

Hey, thank you so very much. My second day with Ubuntu and I love the interface already. I'm doubly impressed by the immense knowledge and helpfulness of the people here. If there are any reading suggestions and in what order for a totally green Ubuntu user, please let me know. I'd really like to be able to contribute as much as I can to this freeware effort. This stuff is wonderful!

---

### Post by baylessiii on 2008-06-19
Yikes! Stuck in low graphics mode. Any idea how to get out of this pickle? Thank you.

---

### Post by baylessiii on 2008-06-19
Okay!! Time for some pizza! It all worked out great, gang. Thanks again. I just opened up the xorg.conf console, made the modifications steps 8 - 12 called for and told Gimp about it. Intous 2 working perfectly! The mistake I made was leaving in
 Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
My first clue should have been that I don't have a tablet pc, but hey, I'm catching on. Hungry to learn all I can about this stuff, and for pizza. Again, totally amazed and thankful there are people here sharp enough to make this happen and kind enough to share it.

---

### Post by drummingpariah on 2008-06-19
> **baylessiii said:**
> Again, totally amazed and thankful there are people here sharp enough to make this happen and kind enough to share it.

Isn't that what makes linux what it is?  Share the love, whenever you find something good or have a good idea, pass it along.

---

### Post by bonfire89 on 2008-07-09
> **AlumaSqrl said:**
> I've tried the Twinview and ScreenNo options with and without xinerama.  
They don't seem to have any effect on the problem in my case.  As the effectiveness of stable solutions seems to vary so widely, I'm beginning to suspect it might be something else... like the xorg video drivers for my geriatric Voodoo5.  I've sorted through - and updated - all the relevant wacom-related files and drivers i know about.  Either there's something else that controls how xorg handles events, or there's something interfering.

That's just my suspicion.

screenNO has no effect with me either :(

---

### Post by RemcoBoerma on 2008-07-17
Thanks for the great recipe on how to set up the tablet! 

I've got mine working, with pressure sensitivity, but also with some problem. I've used an old Wacom ET-0405-R (serial interface only) apparantly from the Graphire series. 

All functionality is there, but the problem is that i get more functionality then i bargained for. . . It seems to me some kind of clock-tick is in the way "pressing" my tablet. . . A graphic example will show this best.  See the screenshot. 

I've tried setting something like ```
Option "PressCurve" "50,0,100,50
``` but that also didn't help a thing. 

Any help is appreciated - TIA

Xorg.conf: 
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Type"          "eraser"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
EndSection


Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 1024
        Depth       24
        Modes      "1280x1024@75" "1280x1024@60" 
    EndSubSection
EndSection

```

---

### Post by Pokkulompus on 2008-08-09
Works great!

---

### Post by paradexes on 2008-08-10
FYI Manga Studio EX 3.0 works under WINE. I followed this guide for pressure sensing and it works great!! Thanks :D

---

### Post by Pokkulompus on 2008-08-10
I managed to get the pen to work, but it moves slow and only when i press it against the tablet. Is it supposed to work like that or what did i do wrong? Help me, please!

---

### Post by savanik on 2008-12-28
I'm still having problems getting my tablet PC's stylus working. I've been following the instructions outlined on The Linux Wacom Project.

So far I have:

Verified that I am running with current updates
Have all the proper libraries loaded
Verified that the prebuilt modules will work with my kernel version (2.6.27-9-generic)
Installed the Wacom driver with the install script from linuxwacom-0.8.2 (most recent I could find)
Confirmed with 'wacdump' that it is picking up my stylus
Identified my stylus as /dev/ttyS1
Edited /etc/X11/xorg.conf in what should be the proper manner
Restarted X in the shell to watch error messages

And I'm still getting this:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
dlopen: /usr/lib/xorg/modules/input//wacom_drv.so: undefined symbol: xf86errno
(EE) Failed to load /usr/lib/xorg/modules/input//wacom_drv.so
```

From what I understand, people are saying that the extra // doesn't matter, it's the xf86errno that matters. I've tried compiling and installing the module myself, but that doesn't seem to change matters. What output could I post up for people to help me? I'm tossing up my xorg.conf as a text file to start with.

It's a Gateway m275 Tablet PC, btw.

Sincerely,
Savanik

---

### Post by Favux on 2008-12-28
Hi savanik,

Another M275 owner, MGaddict2000, has been struggling to get going too at:

[http://ubuntuforums.org/showthread.php?t=967147&page=8]("http://ubuntuforums.org/showthread.php?t=967147&page=8")

You should get in touch.  Also it's always worth trying these sites:

[https://wiki.ubuntu.com/LaptopTestingTeam/]("https://wiki.ubuntu.com/LaptopTestingTeam/")

[http://www.linux-on-laptops.com/]("http://www.linux-on-laptops.com/")

[http://tuxmobil.org/]("http://tuxmobil.org/")

And Loic2's wiki on wacom drivers:

[https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver")

I've included MGaddict2000's xorg.conf to show where he was.  You folks (M275) owners might want to start your own thread, if there isn't one already.

Found a good thread, this guy would be good to get into contact with:

[http://ubuntuforums.org/showthread.php?t=984634&highlight=tablet+pc]("http://ubuntuforums.org/showthread.php?t=984634&highlight=tablet+pc")

---

### Post by savanik on 2009-01-03
I took another crack at it with my M275 and found that the module I had in the directory wasn't the one I compiled! It appears the install script flubbed somehow. After copying the compiled module into the proper directory, everything started working perfectly.

Then I just had to write some scripts with xrandr and xsetwacom to rotate the screen and rotate the stylus input properly. It's too bad it doesn't automatically do that, but I can deal with clicking on an icon.

savanik

---

### Post by Loghtyrian on 2009-04-11
Hi:

I'm a new user of Ubuntu, I'm trying to get my Bamboo Tablet set up to work with it and i've followed the instructions found in this thread but after changing my xorg.conf and rebooting I get an error and Ubuntu starts at low graphics mode plus the tablet doesn't  respond. Any idea or what the problem may be?

This is how my xorg looks like now without any change:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by Favux on 2009-04-11
Hi Loghtyrian,

I'm going to assume you are using Intrepid from your xorg.conf.  The attached xorg.conf should work for you.  Be sure to back up your current xorg.conf.  Also compare the two before using so you can review the changes and can correct any obvious mistakes I made.

Since you are new ask me if you have any questions about backing up, etc.

---

### Post by Loghtyrian on 2009-04-14
Hi Favux,

Thanks for the aid, I have my pen working now with Ubuntu, but now the mouse of the tablet doesn't respond :lolflag: any idea if I can get the mouse to work too?

THANKS ! ! !

---

### Post by Favux on 2009-04-14
Hi Loghtyrian,

Sorry, I didn't realize it came with a Wacom mouse.  Are there different Bamboo models or was it an option?

Also to set up your tablet buttons see post #7 here:  [http://ubuntuforums.org/showthread.php?t=1098822](http://ubuntuforums.org/showthread.php?t=1098822)

Anyway try this xorg.conf.  Same cautions as before.

---

### Post by Loghtyrian on 2009-04-14
It's a Bamboo Fun Tablet, it comes with the mouse. Thanks for your help Favux now i got my tablet fully functional. I tried with the Gimp and works fine.

I really apreciate your help.

THX ! ! !

---

### Post by Favux on 2009-04-14
You're welcome.  Have fun.

---

### Post by Jordanwb on 2009-04-18
I was thinking of getting on of these so I just might. Bookmarked.

---

### Post by loklaan on 2009-04-26
I have a Bamboo Fun small 4x5, and took the instructions from the first page and had them work for me in GIMP, but the problem is when I dont have the tablet plugged in, errors come up about not finding the tablet and being unable to start X...

I have a Bamboo Fun

---

### Post by Favux on 2009-04-26
Hi BuNsiE,

Jaunty uses the HAL/.fdi method.  So you don't need to add the Wacom sections to xorg.conf like the tutorial up front does.  The Wacom stuff is in 10-wacom.fdi.  So if you changed your xorg.conf that may be the problem.

---

### Post by loklaan on 2009-04-26
Oh ok, I changed my xorg.conf then, and I'll look into what you said. Thanks Favux!

---

### Post by loklaan on 2009-04-26
> **Favux said:**
> Hi BuNsiE,

Jaunty uses the HAL/.fdi method.  So you don't need to add the Wacom sections to xorg.conf like the tutorial up front does.  The Wacom stuff is in 10-wacom.fdi.  So if you changed your xorg.conf that may be the problem.

I reinstalled my hal packages and wacom-tools, but my bamboo fun still acts like a mouse - no pressure sensitivity etc...

---

### Post by Favux on 2009-04-26
Hi BuNsiE,

But the warnings are gone, correct?

In Gimp when you configured input devices did you tell it when doing stylus that mode was screen?  That should get pressure.

The Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

has a link to:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

The 10-wacom.fdi is in /usr/share/hal/fdi/policy/20thirdparty/.  Right now there is a problem with the way linuxwacom 0.8.2-2 drivers and wacom-tools are implemented in Jaunty.  We've figured out a couple work arounds but it looks like they (Ubuntu) are getting ready to fix things.  But I admit I don't know when that will happen.  So I don't know if you want to put a lot of time into it right now.

---

### Post by loklaan on 2009-04-26
I only get three devices when trying to configure Gimp, and they are my mouse, touchpad and mac mouse emulation. The stylus and eraser options are not there...

What should I do to the .fdi to get them working on hotplugging the tablet?

---

### Post by Favux on 2009-04-26
Hi again BuNsiE,

I'm not sure what's going on.  Even with the problems I think you should have stylus (maybe not eraser).  So is something else going on also?  Problem with your tablet hot plugging?  Have you tried booting with it plugged in?  Have you checked that your .fdi file is there?  In Synaptics do you see 0.8.2-2 xorg-xserver-wacom-input and wacom-tools are installed?

I'll point you to the work arounds so at least you have an explanation.  But I think you may be looking at a separate problem.  Read Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  It is possible that you need to do the substitution of the 0.8.3-2 wacom.ko for the 0.8.2-2 one as described in work around 1.  The Bamboo is usb correct?  But be careful and read things through before deciding to do anything.

---

### Post by tjb_15 on 2009-08-01
Great instructions. I was trying to get it to work with the instructions off of the wacom-tools site but that just screwed up the mouse fuction. I reinstalled and now it works exactly like it did in windows!!!!!! Thanks so much.. 

Also I sat here for about 3-4 hours trying to get the eraser and pen to work right in gimp before I realized that I was following your directions incorrectly. I was going into the Input Controllers (and using Linux Inputs) instead of the Input Devices (and using Configure Extended Input Devices...). ](*,) 

Now I just need to get my G15 working. ;-)

---

### Post by sunite on 2009-08-25
hey guys, thanks for all the great info.

However I found something interesting, which finally solved my problem:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700")

---

### Post by jisaac on 2009-09-16
Hi,

Someone manage to get the pressure working under a recent wine (>= 1.1.23)?

Please let me know,

Thanks.

---

### Post by hjvv on 2009-12-07
Hello UbuntuHeads,

I've done this

> sudo apt-get install wacom-toolsBut.... sorry, newby here.... struggling with Ubuntu 9.10 and Wacom Bamboo tablet.... where do I enter the rest of the code? I would really appeciate a hint :)

---

### Post by MechanteAnemone on 2010-06-12
Another set of thanks for the instructions.  I'm new to Linux, installed Ubuntu 10,04, followed the instructions on configuring The GIMP, and Bob's your uncle!  I'm in business again with my Wacom tablet, with buttons remapped to suit my preferences.  I also installed MyPaint, which works really nicely with Wacom devices.

---

### Post by cr0max on 2010-07-28
Hello,

I just can't get this damn thing to work. I'm using Ubuntu 9.10. The stylus doesn't work as a mouse, It's not even recognized, xsetwacom list returns nothing. The only thing thats happening when I plug it in is that the LED of the tablet shines and changes it's color when the stylus is brought near the surface. What's the problem? I have, of course, installed the wacom-tools and the xorg-xserver-input-wacom package.

This is my xorg.conf:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth     24
                Modes    "1024x786"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mouse1"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection 

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event0"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
    Option "PressCurve" "50,0,100,50"
    Option "Mode" "Absolute"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event0"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event0"
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents"
InputDevice   "pad"
EndSection
```Additionally, xserver returns following error when started with that config.
```
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
```I have already tried it with an empty xorg.conf - nothing. xserver-xorg-input-wacom is version 1:0.8.4.1-0

xinput --list shows
```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ImPS/2 Logitech Wheel Mouse"    id=4    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 7
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"AT Translated Set 2 keyboard"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=6    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```xidump -l shows:
```
Virtual core pointer           disabled
Virtual core keyboard          keyboard
Power Button                   extension
Power Button                   extension
ImPS/2 Logitech Wheel Mouse    extension
AT Translated Set 2 keyboard   extension
Macintosh mouse button emulation extension

``````
more /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0005 Version=0051
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103


```

Thanks

---

### Post by cr0max on 2010-07-28
Update:
I've compiled and installed the linuxwacom wacom.ko 0.8.8.8 as described [here](http://frankgroeneveld.nl/2010/04/12/get-wacom-bamboo-pen-working-in-ubuntu-karmic/). Now the tablet is at least recognized by xsetwacom list as
```
xsetwacom list
Wacom_Bamboo_Craft_Finger     stylus

```

grep -i wacom /var/log/messages | tail returns:
```
Jul 28 21:19:02 LHC kernel: [ 2427.704145] input: Wacom Bamboo Craft Pen as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input11
Jul 28 21:19:02 LHC kernel: [ 2427.789496] input: Wacom Bamboo Craft Finger as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.1/input/input12

```

and cat /var/log/Xorg.0.log
```
(II) config/hal: Adding input device Wacom Bamboo Craft Finger
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event6"
(II) Wacom Bamboo Craft Finger: x-axis range 0 - 480
(II) Wacom Bamboo Craft Finger: y-axis range 0 - 320
(II) Wacom Bamboo Craft Finger: pressure range 0 - 1023
(II) Wacom Bamboo Craft Finger: finger width range 0 - 0
(II) Wacom Bamboo Craft Finger: buttons: double triple
(--) Wacom Bamboo Craft Finger: touchpad found
(**) Wacom Bamboo Craft Finger: always reports core events
(II) XINPUT: Adding extended input device "Wacom Bamboo Craft Finger" (type: TOUCHPAD)
(**) Wacom Bamboo Craft Finger: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo Craft Finger: (accel) filter chain progression: 2.00
(**) Wacom Bamboo Craft Finger: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo Craft Finger: (accel) set acceleration profile 0
(--) Wacom Bamboo Craft Finger: touchpad found

```

STILL the stylus doesn't do anything. any idea?

---

### Post by Favux on 2010-07-28
Hi cr0max,

Welcome to Ubuntu forums!

What tablet model do you have?  Your xorg.conf in the first post is missing the pad section which is probably the parse error.  Are you also using a 10-linuxwacom.fdi?  That should be located at /usr/share/hal/fdi/policy/20thirdparty/.  You should use one or the other.  The .fdi let's you hot plug.

---

### Post by cr0max on 2010-07-29
Thanks Favux,

yes I'm using /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi from linuxwacom 0.8.8-8 and in the xorg.conf right now only 
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth     24
                Modes    "1024x786"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
EndSection
```No movement though. This really really sucks :(

Strange thing:
xsetwacom list returns nothing (it did yesterday). though wacdump /dev/input/event4 shows some rightish input from the stylus.

I got a bamboo and after rereading first page, I reckon I don't need the pad record. Seemingly you were right about the error either. No movement, though. Do I actually need the xorg.conf under Karmic ?

---

### Post by Favux on 2010-07-29
In Karmic you need the xorg.conf for the Nvidia video sections if you are using the proprietary drivers.  I think you have the Bamboo Fun (CTH661).  Try the .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Also you want to see if the usb kernel driver wacom.ko is auto-loading:
```
lsmod | grep wacom
```
If you don't see wacom try adding it the the modules file in /etc/

---

### Post by cr0max on 2010-07-29
> **Favux said:**
> In Karmic you need the xorg.conf for the Nvidia video sections if you are using the proprietary drivers.  I think you have the Bamboo Fun (CTH661).  Try the .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Also you want to see if the usb kernel driver wacom.ko is auto-loading:
```
lsmod | grep wacom
```If you don't see wacom try adding it the the modules file in /etc/
Oh pardon me, the model is CTH-461.
Does the xorg-entry for the nvidia drivers interfere with the .fdi ? I now have your .fdi in use, but xsetwacom list returns
```

touch            touch    

```no stylus.
xinput --list only returns touth too:
```
"touch"    id=6    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 480
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 320
        Resolution is 1

```

lsmod | grep wacom returns
```
wacom                  33660  0 

```

thanks

---

### Post by Favux on 2010-07-29
Hi cr0max,

OK, it looks like your linuxwacom drivers aren't working.  The touchpad is either coming from the Synaptic .fdi/driver, in which case we need to fix the Synaptic .fdi, or the evdev .fdi/driver.  Once 'xinput --list' shows stylus, eraser, touch, and pad and 'xsetwacom list' agrees with it you should be good to go.

The way to find out what's going on is to look at Xorg.0.log in /var/log.  Go ahead and post it as an attachment.

Do you have a 64-bit install?  Is your kernel something other than the generic?

---

### Post by cr0max on 2010-07-29
Hello Favux,

The kernel is the normal 32 bit.

I think here we really have the problem...
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(WW) Warning, couldn't open module wacom
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (module does not exist, 0)
(EE) No input driver matching `wacom'
```As mentioned it's the 0.8.8-8 linuxwacom wacom.ko

```
modinfo -n wacom
/lib/modules/2.6.31-22-generic/kernel/drivers/input/tablet/wacom.ko

```Thanks for your efforts.

---

### Post by Favux on 2010-07-29
Sure.

You're right.  That could mean there's something wrong with the linuxwacom X driver.  Synaptic is showing up.  I'm not sure if it's causing a problem or not but let's fix it first.  The changes to it's .fdi won't hurt anything and it'll eliminate a variable.  Don't worry if touch disappears from 'xinput --list' afterwords.  See:  [http://ubuntuforums.org/showpost.php?p=8372380&postcount=22](http://ubuntuforums.org/showpost.php?p=8372380&postcount=22)

---

### Post by cr0max on 2010-07-29
> **Favux said:**
> Sure.

You're right.  That could mean there's something wrong with the linuxwacom X driver.  Synaptic is showing up.  I'm not sure if it's causing a problem or not but let's fix it first.  The changes to it's .fdi won't hurt anything and it'll eliminate a variable.  Don't worry if touch disappears from 'xinput --list' afterwords.  See:  [http://ubuntuforums.org/showpost.php?p=8372380&postcount=22](http://ubuntuforums.org/showpost.php?p=8372380&postcount=22)

Ok the .fdi looks like this now:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">
        <merge key="input.x11_driver" type="string">synaptics</merge>
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by cr0max on 2010-07-29
After a restart the Xorg.0.log still contains the same error message.
By the way: shouldnt modprobe -v wacom return an error too ?

---

### Post by Favux on 2010-07-29
Alright.  The question is, is it the right wacom.ko?  When I lsmod the 0.8.8-8 I get:
```
wacom                  45568  0
```
Notice the size difference from what you posted.  So either you didn't copy the compiled wacom.ko correctly or something went wrong with the compile.  Like not including the right dependencies.  Did you need hid-ids.h?  Karmic is unique in requiring that.  That's the alternate step 3 in Section 1.  See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by cr0max on 2010-07-29
Is that ok?
```
./configure --enable-wacom --prefix=/usr | grep no
checking for gawk... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether we are cross compiling... no
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether -lc should be explicitly linked in... no
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.7 or later... no
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... no
checking X11/extensions/Xrandr.h presence... no
checking for X11/extensions/Xrandr.h... no
no
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes
     XFree86 source - no 
          XSERVER64 - no
         xf86config - no
          wacomxrrd - no
              hid.o - no 
        wacom_drv.o - no

```You write
> For **Karmic** use:```
sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```the linuxwacom 0.8.8-8 doesn't have /src/2.6.31/ so I'm using /src/2.6.30/ is that ok ? I don't know if I needed hid-ids.h, I just downloaded it following your instructions.

---

### Post by Favux on 2010-07-29
Looks OK so far.  I need to see the section where it tells us what it'll build after:
```
checking if gcc accepts -fno-stack-protector... yes
     XFree86 source - no 
          XSERVER64 - no
         xf86config - no
          wacomxrrd - no
              hid.o - no 
        wacom_drv.o - no
```
But if there is a wacom.ko now in /src/2.6.30/ you should be OK.  If it didn't compile it wouldn't be there.  They've been consolidating the folders where the wacom.ko is placed, which is why it's so confusing.  But /src/2.6.30/ should be the right place now.

---

### Post by cr0max on 2010-07-29
I better post the whole thing:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-22-generic/build
checking kernel version... 2.6.31-22-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... no
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... no
checking X11/extensions/Xrandr.h presence... no
checking for X11/extensions/Xrandr.h... no
no
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.31-22-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------


Your wacom.ko will be available under 
    /home/mux/linuxwacom-0.8.8-8/src/2.6.30

```thanks

btw, take a look at this ```
modinfo -d wacom
USB Wacom tablet driver
USB Wacom tablet driver

```
= two drivers ?

---

### Post by cr0max on 2010-07-29
```
lsmod | grep wacom
wacom                  33660  0 

``````
/lib/modules/2.6.31-22-generic/kernel/drivers/input/tablet$ ls -l | grep wacom
-rw-r--r-- 1 root root 46915 2010-07-29 19:47 wacom.ko

```Isn't this strange ?

After another compilation of linuxwacom 0.8.8-8 xsetwacom lists the stylus, at least. nothing more, though. and no movement.

---

### Post by Favux on 2010-07-29
Good.
```
 BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.31-22-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins

```
Is telling you it is ready to build the usb kernel driver wacom.ko:
```
wacom.o - yes
```
and the X driver:
```
wacom_drv.so - yes /usr/lib/xorg/modules/input
```

Don't worry about the 'modinfo -d wacom'.  That's what it's returning now, instead of the more informative output.  I don't know why.

---

### Post by cr0max on 2010-07-29
So the error is gone
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux LHC 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=b108434f-97f8-44cf-a06b-b52f0889e0c8 ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 29 19:49:53 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:3:0:0) 10de:0201:1043:4057 nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xd0000000/16777216, 0xd8000000/67108864, 0xdc000000/524288, BIOS @ 0x????????/65536
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce3 Ti 200 at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.18.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 Ti 200 at PCI:3:0:0:
(--) NVIDIA(0):     LKM (CRT-0)
(--) NVIDIA(0):     Philips 7108 TV Encoder (TV-0)
(--) NVIDIA(0): LKM (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Philips 7108 TV Encoder (TV-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: Philips 7108
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1024x786"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 400
(--) NVIDIA(0): DPI set to (50, 42); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device Wacom Bamboo Craft Finger
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event5"
(II) Wacom Bamboo Craft Finger: x-axis range 0 - 480
(II) Wacom Bamboo Craft Finger: y-axis range 0 - 320
(II) Wacom Bamboo Craft Finger: pressure range 0 - 1023
(II) Wacom Bamboo Craft Finger: finger width range 0 - 0
(II) Wacom Bamboo Craft Finger: buttons: double triple
(--) Wacom Bamboo Craft Finger: touchpad found
(**) Wacom Bamboo Craft Finger: always reports core events
(II) XINPUT: Adding extended input device "Wacom Bamboo Craft Finger" (type: TOUCHPAD)
(**) Wacom Bamboo Craft Finger: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo Craft Finger: (accel) filter chain progression: 2.00
(**) Wacom Bamboo Craft Finger: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo Craft Finger: (accel) set acceleration profile 0
(--) Wacom Bamboo Craft Finger: touchpad found
(II) config/hal: Adding input device Wacom Bamboo Craft Pen
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.8-7 $
(**) Option "Device" "/dev/input/event4"
Wacom got Pid oxd2 
Wacom got Pid oxd2 again
(EE) PreInit returned NULL for "Wacom Bamboo Craft Pen"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "CRT-0:1024x768@1024x768+0+0"
```

But why doesn't it recognize the eraser and cursor ? 

the output of xinput --list
```
"Wacom Bamboo Craft Finger"    id=6    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 480
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 320
        Resolution is 1

```

bye

---

### Post by Favux on 2010-07-29
OK, I'm confused.  It looked good.  You used:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
to copy the wacom.ko into place?

---

### Post by cr0max on 2010-07-29
> **Favux said:**
> OK, I'm confused.  It looked good.  You used:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```to copy the wacom.ko into place?
positive.

edit: as stated, modinfo returns two drivers if I'm not totally misunderstanding it, this would explain the different sizes.
```
[FONT=monospace][/FONT]modinfo -d wacom[FONT=monospace] 
[/FONT]USB Wacom tablet driver[FONT=monospace] 
[/FONT]USB Wacom tablet driver
```

---

### Post by Favux on 2010-07-29
Well, the only one that should matter would be at /lib/modules/`uname -r`/kernel/drivers/input/tablet/.  You could do a find on your drive for wacom.ko and see if there's another one (not in the linuxwacom source code) I suppose.

I'm wondering if you have more than one 10-linuxwacom.fdi at this point.  The duplicate called 10-wacom.fdi maybe?  You only want one.

---

### Post by cr0max on 2010-07-29
No, only one .fdi. :(

---

### Post by Favux on 2010-07-29
And its contents are just the those in the new-working .fdi?

---

### Post by cr0max on 2010-07-29
yes, the one I posted.
what exactly does it actually do, if I may ask ?

---

### Post by Favux on 2010-07-29
> yes, the one I posted.  
what exactly does it actually do, if I may ask ? 
Ahh.  That's the Synaptic .fdi (5-synaptic.fdi?), not the wacom .fdi (10-linuxwacom.fdi).  The wacom .fdi is at post #384 that I linked you to.  It's the new-working one attached to the post.

Well .fdi stands for device information file.  It matches to a device and then configures the device.  The HAL/.fdi stuff was a temporary detour to get usb hotplugging.  You couldn't do hot plugging with the old udev/xorg.conf.  Now with the new udev and .conf files HAL/.fdi is no longer needed for hot plugging.  That starts with Lucid.

---

### Post by cr0max on 2010-07-30
Oh I'm sorry, I thought I had posted the 10-linuxwacom.fdi, but it was indeed the synaptics.fdi. I tried both your 10-linuxwacom and the .fdi from the linuxwacom 0.8.8-8 folder. nothing. If I use yours, it doesn't even show the stylus. :(

---

### Post by cr0max on 2010-07-30
I am now using the 0.8.6-2 driver and your 10-linuxwacom.fdi and at least I can now use the stylus as a mouse. The eraser is still not recognized by xinput and xsetwacom. Also, if I set the stylus to relative instead of absolute, that slows my system down a bit and the lines are a bit zig zag. Is that "normal" ?

---

### Post by Favux on 2010-07-31
> I am now using the 0.8.6-2 driver and your 10-linuxwacom.fdi and at least I can now use the stylus as a mouse. The eraser is still not recognized by xinput and xsetwacom.
Checking Xorg.0.log in /var/log will tell you which driver has the tablet, stylus and eraser.
> Also, if I set the stylus to relative instead of absolute, that slows my system down a bit and the lines are a bit zig zag. Is that "normal" ?
Don't know.  Sounds like more events are being generated in relative.  If you have an older CPU that could/would slow you down.  You could increase the RawSample rate for the stylus.

---

### Post by artik1024 on 2010-08-01
MetalMusicAddict, many thanks for this HOWTO ! But, how to get pressure sensitivity in photoshop CS5 under wine ? it works under Gimp, but not Photoshop ;)

---

### Post by CanopusArchives on 2010-11-26
Absolutely new to Linux, but, my Wacom seems to be working OK except for one thing.  Mouse wheel will only scroll down page no matter which way I turn it.  There seems to be no way to configure mouse wheel.  Even tried installing Pointing Devices from Ubuntu Software Center, but, it won't even launch.

---

### Post by mhope on 2011-02-15
> **artik1024 said:**
> MetalMusicAddict, many thanks for this HOWTO ! But, how to get pressure sensitivity in photoshop CS5 under wine ? it works under Gimp, but not Photoshop ;)

I am also experiencing the "no pen pressure" issue with both Photoshop CS5 (installed by copying registry items and folders from Windows) and Photoshop CS5 Extended Portable. 

As stated by the previous poster, pressure sensitivity works fine in other programs: Gimp, MyPaint, Photoshop CS2 (via Wine). Any thoughts?

---

### Post by Psyphre on 2011-05-24
> **mhope said:**
> I am also experiencing the "no pen pressure" issue with both Photoshop CS5 (installed by copying registry items and folders from Windows) and Photoshop CS5 Extended Portable. 

As stated by the previous poster, pressure sensitivity works fine in other programs: Gimp, MyPaint, Photoshop CS2 (via Wine). Any thoughts?

Exactly the same issue! Its frustrating that I've got photoshop working flawlessly, yet the one thing i need to use in is pen pressure and that doesnt work!

---

### Post by graphius on 2011-09-26
> **mhope said:**
> I am also experiencing the "no pen pressure" issue with both Photoshop CS5 (installed by copying registry items and folders from Windows) and Photoshop CS5 Extended Portable. 

As stated by the previous poster, pressure sensitivity works fine in other programs: Gimp, MyPaint, Photoshop CS2 (via Wine). Any thoughts?

Add another user with this issue.

---

### Post by graphius on 2011-11-10
-bump -
any ideas on this yet? I have asked over at the wine forums, but they seem to be focused on getting it to work. It works, curser, eraser and buttons, but no pressure sensitivity....:(

---

### Post by Ultra Cronic on 2011-11-20
> **MetalMusicAddict said:**
> This HOW-TO is written for USB Wacom Tablet devices.


**_[SIZE=3]The GIMP[/SIZE]_**
- **File**-> **Preferences**-> **Input Devices**-> "Configure Extended Input Devices".
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".

Now you should have pressure sensitivity in The GIMP. :)

Also, a useability note with Gimp:
Each input device (stylus,cursor,eraser) has a completely different set of attributes in Gimp, and in theory, you can even assign a unique serial number to different pens to get even more granularity. You will experience this when you try to use your eraser for the first time. Rather than selecting the eraser tool, you get the rectangle selection tool instead. This is by design, believe it or not. Gimp does not care that its an eraser, just that it's not the pen you were just using. If you choose the eraser tool now, it will remember that for the next time you try to use it. On the plus side, you can set the eraser to be anything, including the Airbrush tool or Clone tool.
-Taken from [The Wacom Help Page.]("http://linuxwacom.sourceforge.net/index.php/howto/main")

  ;)
:guitar::popcorn::P
Kudos to you man, I've been at it all night break and fix crash and burn compiling drivers and YOUR suggestions are the ones that fired it up. Especialy the gimp input settings quoted above.
Many thanx :biggrin:

---

