---
title: "External Monitor Support (Gutsy Gibbon)"
date: 2007-10-17
forum: System76 Support
---

### Post by TheBuzzSaw on 2007-10-17
I am going to fight until I get this working. Tomorrow, the final release of Gutsy Gibbon comes out. I am assuming that at least *some* of the bugs surrounding external monitor support have been addressed. If anyone would like to help me in this endeavor, please say so. I am using the Darter Ultra (daru2).

The current issue is that the new interface for setting up screens and whatnot does not cooperate very well. The best I can do is boot with a monitor plugged in and use it as a duplicate (though larger) view. My hope is to at *least* set the default monitor to my flatscreen. My laptop runs at 1280x800, but my nice monitor runs at 1280x1024 (and it is much larger than my laptop view). Ideally, I would like to come home from work/school, plug in my mouse, keyboard, and monitor, and work that way.

---

### Post by muzcuk on 2007-10-18
Same thing here.. If I may be of any assistance, please do tell.. I think what we really need is some real drivers for 965.. It also is blacklisted by compiz (does work if you override but you can't play any videos.) 
I have a 1440*900 lcd, made it work at that resolution though the native screen got screwed.. Why can't we simply disable the native screen and make the external one primary..? I think that can be done with a small script but I lack the experience to write it.. Any help would be appreciated..

---

### Post by Rex_Mundi on 2007-10-21
There appear to be heaps of threads roughly about the same issue but I like the title of this one. 

My problem is simple. I have an HP DV9055ea laptop with an NVidia 7600 Go graphics card so it's well supported. In Feisty Fawn I managed to get my external 24" BenQ LCD screen to work no worries. Envy is a great tool that made it a doodle. 

However, Gutsy Gibbon only has given me headaches. I can get the laptop screen to work properly with compiz and at the proper resolution BUT I cannot for the life of me get the screen deactivated and have my external screen enabled. I don't have envy installed and I've been using the new graphics and monitor tool in system. I select my video card and the correct LCD screen option (and resolution) for monitor 2 and then selecting it as a default screen or twinview ruins everything. Because when I faithfully log out or reboot and i'm presented with this new video safe mode in super low resolution with mesa video settings and the saga begins anew. I thought this was supposed to be easier now?? I hope for a fix soon. For now it's back to Feisty Fawn.

---

### Post by steveneddy on 2007-10-21
I've been playing with the Screens and Graphics stuff and it won't set up properly and it is a PITA to work with. 

And why can't I install nvidia-settings without uninstalling the nvidia-glx-new video driver?

With Feisty, nvidia-settings would let you set up an external monitor or projector with little work, and this new bullet proof X sucks.

---

### Post by thomasaaron on 2007-10-22
This is definitely an Ubuntu-related bug.

When you see the splash screen, you can use Fn-F2 to toggle the displays until only the external monitor is displaying. But when the Ubuntu splash screen appears, it reverts back to mirroring. This should be fixable, but I'd suggest filing it as a bug report here:

[https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by TheBuzzSaw on 2007-10-22
I am going to install the full version of Gutsy Gibbon later today. I will report anything I discover (I will also attempt an external monitor setup).

---

### Post by Laen on 2007-10-22
> **thomasaaron said:**
> This is definitely an Ubuntu-related bug.

When you see the splash screen, you can use Fn-F2 to toggle the displays until only the external monitor is displaying. But when the Ubuntu splash screen appears, it reverts back to mirroring. This should be fixable, but I'd suggest filing it as a bug report here:

[https://launchpad.net/system76](https://launchpad.net/system76)

I don't think it's Ubuntu to be honest. When the splash screen appears the X drivers have loaded and that's when the mirroring happens. Before that you can switch between displays because your hardware allows it. I've had the same issue with other distros, so I'm guessing it's the video drivers (in my case intel 945gm's).

Of course I may be completely wrong also.

---

### Post by TheBuzzSaw on 2007-10-22
Wow, explain this to me.
[img]http://thebuzzsaw.googlepages.com/sagp1.png[/img]
Why do I have two "Screen 1"s? Whenever I click either of the other screens, everything is disabled except for the "Default screen" and "Disabled" options. It won't give me the option for enabling a second monitor for any reason. :(

---

### Post by TubaTodd on 2007-10-22
I've had several external monitor problems. First, compiz doesn't recognize the proper screen resolution. At random, when I boot with my external monitor only I get a pair of lines on my screen that won't go away. 

The irony is that without my external monitor, 7.10 has been perfect. What gives?

---

### Post by TheBuzzSaw on 2007-10-23
OK, I turned on my laptop this morning, and starting with the login screen, there were hundreds of black dashes all over! They were evenly spaced (clearly a software glitch), and spanned over everything *except* the mouse cursor. Changing the screen resolution didn't fix it, either! I did a reboot, and all is well, fortunately. I was too traumatized to take a screen shot. :P

Anyone else have this happen before? :(

---

### Post by palintheus on 2007-10-23
> **TheBuzzSaw said:**
> OK, I turned on my laptop this morning, and starting with the login screen, there were hundreds of black dashes all over! They were evenly spaced (clearly a software glitch), and spanned over everything *except* the mouse cursor. Changing the screen resolution didn't fix it, either! I did a reboot, and all is well, fortunately. I was too traumatized to take a screen shot. :P

Anyone else have this happen before? :(

This has happened to me about 2-3 times on Feisty and once on Gutsy. A reboot always fixed it, but yes, it bothered me too.

---

### Post by buntunub on 2007-10-23
:popcorn:


](*,)

Same problem with the dual screens and Screens and Graphics utility hosing down my system something fierce! nvidia-settings does work now, albiet not well. Im thinking an xorg rebuild and manual configs might shed some light on a few things, but seriously, this is one VERY annoying bug they released with.

---

### Post by cowbean on 2007-10-24
This is how I got things to work on my daru1:

I started with a recommended network update to gutsy from feisty, but at the "restart services" step decided to be clever and restart them myself, because i wanted to save some config files and merge them in by hand later... stupidly i restarted gdm which resulted in the uprgade process getting interrupted.  I dunno if it would have completed in any case, but I ended up doing a clean install, except with my old /home partition intact.

In feisty, I had the computer connected to a Dell 2007fp at 1600x1200.  I didn't seem to be able to get a non-mirrored setup going, so I used that monitor exclusively.

After the upgrade, I still had the same display setup, i.e., 1600x1200 external monitor, laptop display mirroring it (somewhat uselessly).

I was getting some weird display output split-up in compiz effects, such as zooming and most annoyingly, maximizing windows.  So, I decided to try to get dual monitors working, or at least, turn on mirroring.

So I mucked around with the Screens and Graphics dialog, often getting kicked back to "low resolution gnome -- manually configure?" window at boot up.

Eventually, I discovered that if I set the driver to intel experimental and monitor to plug and play, it would detect the 1200x800 resolution of the laptop, and mirror that on the external monitor.  From there, I changed the monitor to "Generic - LCD Panel 1600x1200".  I may have been kicked back to the low resolution gnome dialog, where i just repeated these settings.  This resulted in the laptop monitor turning off, and just the external monitor showing up at the desired resolution of 1600x1200.

which is almost what i wanted.  The compiz weirdness has gone away, and I can use the external monitor at the desired resolution.  I just wish multiple, non-mirrored monitors would work too.

[IMG]http://railcannon.net/Screenshot-screenprefs.png[/IMG]

---

### Post by TheBuzzSaw on 2007-10-25
At this point, I am unconvinced that Gutsy Gibbon truly features multimonitor desktops. Sure, it's a good starting point for development, but I have had no success. On top of that, I have heard no amazing success stories from anyone else. If anything, there seems to be more success with Twinview running on Feisty Fawn.

I will make periodic attempts as I learn more about my setup, but methinks Hardy Heron will be the answer to this one... maybe...

---

### Post by TubaTodd on 2007-10-26
I've been experiencing horizontal lines on my external monitor when using Gutsy. There are 2 thin lines that appear, 1 on the left towards the bottom and 1 on the right about 3" above the other line. They appear to be in sync with one another. If I drag a window around on the screen, the lines change size and color while I'm moving the window.  

I ran a bunch of tests last night. Here's what I've figured out so far. Hopefully someone can clue me in on WHY this is happening.

1. If I boot off the 7.10 CD and use my external monitor only, my monitor works fine.
2. If I boot off the 7.10 CD with my external monitor only AND **move my mouse while it is loading** the lines appear
3. I compared the xorg.conf files generated during each bootup and they were identical.
4. If I boot off the Fedora 8 Test 3 CD and use my external monitor only, my monitor works fine.
5. If I boot off the Fedora 8 Test 3 CD with my external monitor only AND**move my mouse while it is loading** the lines appear
6. I compared the xorg.conf files generated during each bootup and they were identical.
7. If I boot from my Ubuntu 7.04 HD installation and move the mouse....the video is fine.


So, it appears that it could be tied to the mouse and perhaps only in newer versions of the OS (ie newer xorg, newer drivers, etc). I'm not 100% certain that this is an exact pattern or correlation, however this pattern happened pretty consistently when I performed each of the above steps (1 - 7) several times last night. If I use my built-in laptop monitor, Gutsy looks to be the best OS I've ever used. I'd love to upgrade to 7.10, but not having my 22" monitor functioning at 100% is not an option.

Any ideas?

Thanks

---

### Post by SyncMaster on 2007-11-04
For me the 
At the beginning, nothing worked really as expected (the Graphics Card wasn't as expected, I experimented for a few hours) 
1) "Profile" Switch doesn't work as expected 
2) Sometimes I get weird parameters for selection, like not showing the correct 1024x768 for the LCD or 61 Hz
3) Just logging out brings me sometimes a 800x600 resolution, sometimes the "emergency" configuration box telling me that the resolution is not right and if I would like to change it
4) ctrl-alt-backspace often does the change much better, I get the 1024x768 on  my lcd.
5) The Icons of the desktop appear on the secondary screens, the menu stays on the default

For profiles: I need three settings (on the laptop): travelling (only LCD), dual (external screen with 1600x1200), and mirrored (for presentations at work)

So far the tool is a nightmare. I can not even reproduce the stuff. Also the profile selection box does not show you what was loaded.

This was a reason for upgrading to 7.10, but with killing the X Server to make it change (at work for a presentation!) it is not practical.


Hardware: 3 year old Centrino laptop with intel 8525 chipset for graphics

---

### Post by victorgreen on 2007-11-21
I have a Lenovo x61 (intel x3100 graphics) and a brand new 20in lcd. The thing runs great except I was hoping to be able to get ubuntu to turn off the laptops screen and exclusively use the external monitor [when its connected that is]. The laptop run at 1024x768 and the external runs at 1680x1050. As of right now the laptop is mirroring the external, including mirroring its resolution so that the the little 12in screen displays only the top left portion of what the external monitor displays.

This causes weird artifacts during cube rotation in Compiz in that there is a line on the external showing the area also displayed on the laptop. This only happens during cube rotation.

---

### Post by cowbean on 2007-11-21
> **victorgreen said:**
> I have a Lenovo x61 (intel x3100 graphics) and a brand new 20in lcd. The thing runs great except I was hoping to be able to get ubuntu to turn off the laptops screen and exclusively use the external monitor [when its connected that is]. The laptop run at 1024x768 and the external runs at 1680x1050. As of right now the laptop is mirroring the external, including mirroring its resolution so that the the little 12in screen displays only the top left portion of what the external monitor displays.

This causes weird artifacts during cube rotation in Compiz in that there is a line on the external showing the area also displayed on the laptop. This only happens during cube rotation.

I think I was able to get rid of that problem by changing the "Outputs" section of the compizconfig settings manager.  It's under the "Display Settings" tab of the General Options group (at the top).

The other way to fix this, and what i ended up doing, is to go the ubuntu menu System -> Administration -> Screen and Graphics, and set the default laptop monitor (represented by the laptop icon) to "LCD Panel [geometry]", and set the resolution to the desired one.  This will probably prompt you to log out, and then you might get kicked back to this config screen, saying that you need to reconfigure.  Just tab over and make sure the driver is set to the one you want, and set the settings to LCD Panel [geometry], and the appropriate resolution.  At least, this is what worked for me.  :)

---

### Post by brettr on 2007-11-21
If you want to turn off the Local Laptop Monitor you can use this
```

xrandr --output LVDS --off
```

Check these out for some more info. 

[http://www.intellinuxgraphics.org/dualhead.html]("http://www.intellinuxgraphics.org/dualhead.html")
[http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head]("http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head")

---

### Post by thomasaaron on 2007-11-23
Yes, I've seen that several times in our shop.

I've never been able to make it happen more than one time on the same machine.

That said, it never happens (as far as I've seen) at the BIOS level -- only in the OS.
So, I agree with you that it is a software glitch. Since it happens so rarely, I've never really been able to diagnose it.

---

### Post by victorgreen on 2007-11-25
Thanks so much brettr, that command worked great!

---

### Post by lmp3 on 2007-12-05
**victorgreen**: i also have a thinkpad X61 running Gutsy (fresh install) but am not able to get my external monitor working properly   :(

could you please** post your xorg.conf** file?

thanks in advance!

---

### Post by victorgreen on 2007-12-07
Well I now have an external monitor and it works great. Just plugged in, restarted and everythings peachy. Not sure what changed but Im not complaining. 

Heres my xorg.conf

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
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"	"ExplorerPS/2"# IMPS/2 is not recommend for TrackPoints
	Option		"Device"	"/dev/input/mice"
	Option		"EmulateWheel"	"on"
	Option		"EmulateWheelTimeout"	"200"
	Option		"EmulateWheelButton"	"2"
	Option		"YAxisMapping"	"4 5"
	Option		"XAxisMapping"	"6 7"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@60"	"1792x1344@60"	"1600x1200@65"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"800x600@56"	"800x600@60"	"1024x768@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by Ryupower on 2008-03-26
> **brettr said:**
> If you want to turn off the Local Laptop Monitor you can use this
```

xrandr --output LVDS --off
```

Check these out for some more info. 

[http://www.intellinuxgraphics.org/dualhead.html]("http://www.intellinuxgraphics.org/dualhead.html")
[http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head]("http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head")

ZOMGAH! That command made miracles happen! My external monitor works now!

---

### Post by imhavoc on 2008-03-26
> **brettr said:**
> If you want to turn off the Local Laptop Monitor you can use this
```

xrandr --output LVDS --off
```

Check these out for some more info. 

[http://www.intellinuxgraphics.org/dualhead.html]("http://www.intellinuxgraphics.org/dualhead.html")
[http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head]("http://ubuntuforums.org/showthread.php?t=581947&highlight=Dual+Head")

I don't know how I missed this. xrandr opens up the external VGA connection easy as pie!

When I run

```
xrandr -q
```
on my Daru2, I get the following output:
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1680 x 1680
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 261mm x 163mm
   1280x800       60.0*+   60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 disconnected (normal left inverted right)
TV disconnected (normal left inverted right)

```

I'm interested to know if the last two lines tell me anything useful about the HDMI output?

---

