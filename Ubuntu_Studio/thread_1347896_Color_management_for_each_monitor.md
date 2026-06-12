---
title: "Color management for each monitor???"
date: 2009-12-06
forum: Ubuntu Studio
---

### Post by CHaoSlayeR on 2009-12-06
Hi *,

I just wondered why there are always options to adapt color management settings for specific "screens" or "displays" but never for "monitors".

To me it doesn't make sense at all to specify color management for such virtual things like "screens" or "displays" because every "monitor" differs.

Is there another way?

I tried:

- xicc
- xcalib
- "gamma" setting in KDE4 system settings
- xf86gammacfg (actually used by system settings)

E.g. at work I have a 30" LCD and a 22" CRT and both need completely different setups but I didn't find a way to specify so until now.

Thanx for any help,

C]-[aoZ

---

### Post by markbuntu on 2009-12-08
At the native resolution of the monitor the screen/display and monitor are the same but the xserver does not really know what this is, it is only capable of rendering screens/displays in its software so that is where the adjustments are necessarily made. 

Many monitors have built in controls for gamma correction etc and it is always better to use those to adjust the monitor because they will change the hardware more permanently to true color rendering. (You should use benchmark color swatches etc when doing this.) That way if a color is off you can quickly check if the monitor has changed of if it is software issues.

This can be very time consuming but you only need to do it once in a great while.( It is good to check CRTs every six months or so as they get older and change more than a LCD).

---

### Post by CHaoSlayeR on 2009-12-08
Hey, I just found a possibility.

To configure the NEC FE 1250+ 22" CRT I've attached to the notebook when I'm at home I can use the following to load a profile for only that monitor without touching other monitors (in my case the internal DFP of the notebook):

```
dispwin -d 1 -I n-fe25p1.icm
```

Unfortunately if I specify a different gamma for the overall system the loaded profile get lost as soon as I e.g. play a video file with (g|k|s)?mplayer.

So it is possible somehow.

But I think the main point is that even the new KDE4 System Settings is not aware of the monitors regarding color management. Although it is aware of them through randr in "Size & Orientation" but in "Gamma" you only have the option the specify the settings per "screen" which means randr screen which means... nothing.

For the next big release this should be fixed and there should be the possibility to load an .cal, .icc or .icm file for each monitor that gets loaded and applied.

This would be really nice as more and more 2D/3D/photo experts are moving to linux or at least giving it a try.

As a good news there is a KDE module for exactly that and beyond (including scanners and printers) to provide a consistent color management in one place for the whole system (as it should):

[http://websvn.kde.org/trunk/playground/graphics/kolor-manager/](http://websvn.kde.org/trunk/playground/graphics/kolor-manager/)

And as it just uses existing bits like elektra or oyranos there is hope that we will see something convenient in the next few years.

So far, cheers,

C]-[aoZ

P.S.: Found a website with some ICC profiles (for those lazy and impatient): [http://www.tftcentral.co.uk/articles/icc_profiles.htm](http://www.tftcentral.co.uk/articles/icc_profiles.htm)

---

### Post by prokoudine on 2010-01-26
> **CHaoSlayeR said:**
> Hi *,

I just wondered why there are always options to adapt color management settings for specific "screens" or "displays" but never for "monitors".
Honestly, I don't understand the problem. Screen is pretty much the same thing as monitor for dualhead configurations, and you don't have multiple screens in single-head configuration.

[GNOME Color Manager]("http://live.gnome.org/GnomeColorManager") along with Argyll solve the color management setup for displays (okay, monitors, if you really like this word :)) just fine. You only need a measurement device which you can get at a range of prices from 90 USD to 400+ USD,

You can read a review [here]("http://libregraphicsworld.org/articles.php?article_id=11") to understand better what it does. If you don't want using GNOME, that's, of course, another story, and I wouldn't dream of arguing about desktops :)

---

### Post by CHaoSlayeR on 2010-01-29
> **prokoudine said:**
> Honestly, I don't understand the problem. Screen is pretty much the same thing as monitor for dualhead configurations, and you don't have multiple screens in single-head configuration.

Well, that's completely wrong, because since xrandr you usually have one screen but multiple monitors. It's the way xrandr works commonly. If you have multiple graphics cards in use you usually have one screen per gfx card, but you usually have one or more monitors per screen.

An example from my laptop:
```
laptop$ xrandr
Screen 0: minimum 320 x 200, current 2880 x 1200, maximum 4096 x 4096
VGA-0 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 396mm x 297mm
   1600x1200      85.0*+   75.0
   1920x1440      72.0
   1792x1344      75.0
   1280x1024      85.0     75.0
   1280x960       85.0
   1152x864       75.0
   1024x768       85.0     75.1     70.1     60.0     43.5
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        72.8     75.0     66.7     60.0
   720x400        87.8     70.1
LVDS-0 connected 1280x800+1600+400 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.1*+
   1024x768       59.9
   800x600        59.9
DVI-D-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
```

And so if you load presets for a screen it gets applied to all monitors within this screen, therefore making it completely useless, because one monitor now looks fine but all the others don't.

For calibration I am using a colorimeter, of course. But the problem is the same when those captured presets have to be applied somewhere.

I don't know what the term "display" exactly refers to in the gnome color manager. If it refers to a "monitor" section in the xorg.conf, than it is fine.

C]-[aoZ

---

### Post by prokoudine on 2010-01-29
> **CHaoSlayeR said:**
> Well, that's completely wrong, because since xrandr you usually have one screen but multiple monitors.
Point taken :)

> **CHaoSlayeR said:**
> I don't know what the term "display" exactly refers to in the gnome color manager. If it refers to a "monitor" section in the xorg.conf, than it is fine.
GNOME Color Manager relies on XRandR (1.2 for single-head, 1.3 for dual-head), in case you didn't read the review :)

And you can set different profiles for different displays with both G-C-M and xicc.

---

### Post by CHaoSlayeR on 2010-01-29
Well I have read the review and also read that the GCM uses udev and EDID data to find/manage devices so it must somehow "speak" rather directly with the devices. It actually doesn't "rely" on xrandr. I think the only thing it uses xrandr for is the layout of multiple monitors/screens.

And xicc is not able to deal with monitors directly. It can only apply profiles to X displays (which is even worse than screens). The X display is the X session you're running with including all screens and monitors. In nearly all cases you're running only one X display at a time (of course in multi-user environments this can be thousands).

Sorry to correct things one more time.

As I said earlier I already tried xicc:
```
Usage:
  xicc [OPTION...] PROFILE - set an ICC profile on a screen

Help Options:
  -h, --help                Show help options

Application Options:
  -d, --display=DISPLAY     X display to use
  -s, --screen=SCREEN       X screen to use
```

...dispwin is much better here:
```
Test display patch window, Set Video LUTs, Install profiles, Version 1.0.3
Author: Graeme W. Gill, licensed under the GPL Version 3                  
usage: dispwin [options] [calfile]
 -v                   Verbose mode
 -display displayname Choose X11 display name
 -d n[,m]             Choose the display n from the following list (default 1)
                      Optionally choose different display m for Video LUT access
    1 = 'Screen 1, Output VGA-0 at 0, 0, width 1600, height 1200'
    2 = 'Screen 2, Output LVDS-0 at 1600, 400, width 1280, height 800'
 -p ho,vo,ss          Position test window and scale it
 -F                   Fill whole screen with black background
 -i                   Run forever with random values
 -G filename          Display RGB colors from CGATS file
 -m                   Manually cycle through initial values
 -f                   Test grey ramp fade
 -r                   Test just Video LUT loading
 -n                   Test native output (rather than through Video LUT)
 -c                   Load a linear display calibration
 -V                   Verify that calfile/profile cal. is currently loaded in LUT
 -I                   Install profile for display and use it's calibration
 -U                   Un-install profile for display
 -S d                 Specify the install/uninstall scope for OS X [nlu] or X11/Vista [lu]
                      d is one of: n = network, l = local system, u = user (default)
 -L                   Load installed profiles cal. into Video LUT
 -D                   Run in daemon loader mode for given X11 server
 -E [level]           Print debug diagnostics to stderr
 calfile              Load calibration (.cal or .icc) into Video LUT
```

So that's why I choose dispwin. So the real straight forward way of handling displays is to just use that tool in the GUIs.

C]-[aoZ

---

