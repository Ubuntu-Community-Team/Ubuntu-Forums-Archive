---
title: "screen resolution darter daru3"
date: 2008-12-05
forum: System76 Support
---

### Post by jdayrutherord on 2008-12-05
Well, while attempting to hook up an external monitor
I used the preferences, screen resolution to
attempt to detect the display which I had connected to the external
vga port. I think I selected 800X600 resolution and it asked to
update a system file.

The end result is that I now only have only 1024, 800, and 640 resolutions
available with 60hz refresh rate. (and still cannot connect the external monitor (samsung lcd).

My /etc/Z11/xorg.conf file is:

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
	SubSection "Display"
		Virtual	2048 777
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


With the external samsung connected xrandr -q shows:

john@ubuntu:/etc/X11$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 777
VGA connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  


When disconnected it shows:

john@ubuntu:/etc/X11$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 777
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
john@ubuntu:/etc/X11$ 

Any tips on getting the 1280 resolutions back? Are there any secrets for getting an external monitor to work? I tried an old dell crt, and the samsung.

Thansk!

---

### Post by drewbenn on 2008-12-06
I'd start by (remembering to back up your xorg.conf first, of course ;)) changing the 'Virtual' line in xorg.conf from "2048 777" to "2048 800". I don't know for sure if that'll bring back your 1280x800 resolution, though.

You'll need to restart X, of course, for the change to take effect: either press ctrl-alt-backspace (save everything you're working on first) and log back in, or just reboot.

As far as hooking up the external monitor, try: ```
xrandr --output LVDS --mode 1024x768 --output VGA --right-of LVDS --mode 1024x768 --rate 60
``` which is _supposed_ to put the external monitor's output to the right of your laptop's output.  You could try removing "--right-of LVDS" and I think it might mirror the laptop display, but I don't have my external monitor hooked up right now to verify that.

I turn it back off later with:
```
xrandr --output VGA --off
```

If you want to use your top resolutions you'll need to increase the width component of the 'Virtual' line in xorg.conf.  So if you want 1280x800 from the laptop and 1360x768 from the external display, change the Virtual line to "1640 800".

Finally: I rarely see responses from System 76 support on weekends, so you may need to wait until Monday to get a useful response.  It will probably help them diagnose what's wrong if you can include your version of Ubuntu and how you got there (e.g. "Ubuntu 8.10, upgraded from 8.04;" or "Kubuntu 8.10 fresh install").  I believe the usage of xorg.conf changed significantly in 8.10, so it's possible that is related.

P.S. when pasting output, if you paste it inside "CODE" blocks (highlight it and press the button with the # icon in this editor) you will preserve line formatting. It's not critical here but is useful for showing things like indentation in the xorg.conf.

---

### Post by jdayrutherord on 2008-12-07
I gave that a try (not the xrandr for the external monitor).
I edited the xorg.conf file

(which is this before the edit)
```
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```
And changed it to 2384 800

That did result in system->preferences->screen resolution allowing me to
select 1280 X 800. But when I did that. logged out, and reloged in it
displayed the extra resolution part of the screen as garbage. the 800 X 600 part was ok.

---

### Post by jdayrutherord on 2008-12-07
Oh, I forgot to mention, I am running 8.10, installed clean with
system 76 drivers added (2.2.7). Uname -r is:

2.6.27-10-generic

Thanks,

---

### Post by thomasaaron on 2008-12-08
Here's how to fix your resolution...

#Backup your xorg.conf...
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-create it... Use ALL defaults
sudo dpkg-reconfigure xserver-xorg

Reboot your computer.
If the resolution isn't right, go to System > Prefs > Screen Resolution and set it to the correct resolution.

---

### Post by nealaustin on 2009-03-19
I am interested in the Darter and have thought of running it with a 19 inch external monitor. I never had a real laptop before but as my computer gets older the prospect is getting closer to reality.>jdayrutherord & thomasaaron< How did the darter run with the external monitor? Is it possible to turn it on without opening the laptop each time? I know that I am hijacking the thread, sorry.

---

### Post by thomasaaron on 2009-03-20
I have a 19" monitor here in the shop that I test with, it works fine with the Darter.

---

