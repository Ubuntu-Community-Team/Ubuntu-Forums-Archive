---
title: "Dual Monitors not working. at all!"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by humanisfood on 2012-10-02
i am using ubuntu 12.10 beta 2 updated regularly.

i have a Acer H274HL (1920x1080 DVI cable) and a small Viewsonic VG150 (1024x768 VGA cable). i also have the GeForce GT430 video card and i am using proprietary drivers and they are up to date.

i have the big Acer hooked up and then i hot plug the small Viewsonic. the Acer turns off and the Viewsonic is now displaying my desktop. I go into Display in System settings and only the Viewsonic shows up. I also go into nvidia-settings and same, only viewsonic monitor available.

i have tried many many things. restarting, using the Acer with a HDMI cable... various "fixes" from the internet. lots of searching and no luck.

when i use the xrandr command it says DVI-I-1 disconnected (normal left inverted right x axis y axis) even though it IS connected and works fine if i only connect the 1 monitor.

if anyone knows anything it would be a great help. thanks so much!

---

### Post by Favux on 2012-10-03
Hi humanisfood,

What is the active (marked with an *) output for the Acer H274HL in the xrandr output when just the Acer monitor is connected?

Is the Viewsonic VG150 rotated?

Have you tried an xrandr command for the Acer after it goes blank to turn it back on?  And by the way does the Acer only go black when you hotplug the Viewsonic?  Or does it also happen when the Viewsonic is plugged in while you boot?

---

### Post by humanisfood on 2012-10-04
> **Favux said:**
> Hi humanisfood,

What is the active (marked with an *) output for the Acer H274HL in the xrandr output when just the Acer monitor is connected?

Is the Viewsonic VG150 rotated?

Have you tried an xrandr command for the Acer after it goes blank to turn it back on?  And by the way does the Acer only go black when you hotplug the Viewsonic?  Or does it also happen when the Viewsonic is plugged in while you boot?

```
$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      60.0*+
   1440x900       59.9  
   1280x1024      60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```

the viewsonic displays normal by itself and when i attempt to get both monitors working.

```
$ sudo xrandr --output DVI-I-1
```
this command executes but nothing happens and i get NO error messages.

only the small viewsonic works while hot plugging as well connecting before bootup.

---

### Post by cromat on 2012-10-04
Not sure if this will help but I am on my Zenbook right now with an intel gfx card, and I can't use dual monitors without any issues through my HDMI connection. It appears to be related to a dedicated graphics cards.

---

### Post by Favux on 2012-10-05
Assuming the Viewsonic is connected and working.  And it is VGA-0 and you intend it to be to the right of the Acer, what happens when you run?
```
xrandr --output DVI-I-1 --auto --mode 1920x1080 --left-of VGA-0
```

---

### Post by humanisfood on 2012-10-05
```
$ xrandr --output DVI-I-1 --auto --mode 1920x1080 --left-of VGA-0
xrandr: cannot find mode 1920x1080
```

---

### Post by Favux on 2012-10-05
I was thinking you might want to turn off the XRandR plugin for the gnome-settings-daemon. Open up a terminal and start dconf-editor, might need to install it.
```
sudo apt-get install dconf-editor
```
Now browse to org.gnome.settings-daemon.plugins.xrandr and uncheck the "active" entry.  It defaults to mirror mode for connected monitors and what usually happens is the resolution on the bigger monitor is lowered until it finds something in common between the two.  I was wondering what happens it couldn't find any resolution in common.  You could of course compare the xrandr output when the Viewsonic is also connected to check on that.

But from "xrandr: cannot find mode 1920x1080" it is looking more like somehow when VGA output (VGA controller?) is used you lose access to EDID?  In which case maybe you need to set a new modeline.  You use **cvt "resolution"** when just the Acer is connected.  See:  [http://ubuntuforums.org/showpost.php?p=10252029&postcount=14](http://ubuntuforums.org/showpost.php?p=10252029&postcount=14)  The other option would be to set everything up in a xorg.conf.

---

### Post by humanisfood on 2012-10-06
> **Favux said:**
> I was thinking you might want to turn off the XRandR plugin for the gnome-settings-daemon. Open up a terminal and start dconf-editor, might need to install it.
```
sudo apt-get install dconf-editor
```Now browse to org.gnome.settings-daemon.plugins.xrandr and uncheck the "active" entry.  It defaults to mirror mode for connected monitors and what usually happens is the resolution on the bigger monitor is lowered until it finds something in common between the two.  I was wondering what happens it couldn't find any resolution in common.  You could of course compare the xrandr output when the Viewsonic is also connected to check on that.

But from "xrandr: cannot find mode 1920x1080" it is looking more like somehow when VGA output (VGA controller?) is used you lose access to EDID?  In which case maybe you need to set a new modeline.  You use **cvt "resolution"** when just the Acer is connected.  See:  [http://ubuntuforums.org/showpost.php?p=10252029&postcount=14](http://ubuntuforums.org/showpost.php?p=10252029&postcount=14)  The other option would be to set everything up in a xorg.conf.

thanks so much for your help. i tried your suggestion and it didn't seem to help.

i did a little more research and got the impression that my video card did not support DVI+VGA dual monitors but that DVI+HDMI would work. I went and bought an adapter and hooked the viewsonic up to the DVI and the Acer to the HDMI. still same issue(only the viewsonic would display)! got fed up and tried another monitor(in place of the viewsonic) and IT WORKED!!!! i guess something is screwy with that Viewsonic. Thanks again for your help! now my dual monitor setup is working fine after i replaced that stupid viewsonic monitor! haha.

---

### Post by ncs_one on 2012-10-11
I have a similar problem but I can't solve it...

My graphics card according to lspci is
```
VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTS 450] (rev a1) 
```It has a DVI and a VGA output. I use the NVIDIA version current drivers.

When I connect a screen (any one of the two I'm trying to connect) to any one of the two ports, it works. When I connect both of them and boot, Ubuntu only sees the one connected to the DVI port. Also, when I boot with just one screen connected (it doesn't matter on which port) and after startup I connect the second screen, nothing happens.

The output of xrandr when I connect only the screen on the VGA port is
```

~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0
   1680x1050      52.0     53.0
   1440x900       54.0
   1400x1050      55.0     56.0
   1360x768       57.0     58.0
   1280x1024      59.0     60.0
   1280x960       61.0
   1152x864       62.0     63.0     64.0     65.0
   1024x768       66.0     67.0     68.0
   960x600        69.0
   960x540        70.0
   840x525        71.0     72.0     73.0     74.0
   832x624        75.0
   800x600        76.0     77.0     78.0     79.0
   720x450        80.0
   700x525        81.0     82.0
   680x384        83.0     84.0
   640x480        85.0     86.0     87.0     88.0
   512x384        89.0     90.0
   400x300        91.0
   320x240        92.0     93.0

```The output of xrandr when I connect only the other screen on the DVI port is:
```

~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0     51.0     52.0* 
   1280x960       53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0     73.0  
   720x450        74.0  
   700x525        75.0     76.0  
   680x384        77.0     78.0  
   640x480        79.0     80.0     81.0     82.0     83.0     84.0  
   512x384        85.0     86.0  
   400x300        87.0  
   320x240        88.0     89.0  

```When both of the screens are connected, xrandr gives the same output as in the second case. It's like the screen on the VGA port doesn't exist.

I also tried connecting the first screen on the DVI port and the second screen on the VGA port, but the result is similar: when both are connected, only the one on the DVI port works.

One last point, I used dual screen setup on the same computer (one screen was the same as this time) using Ubuntu 11.04 and it worked perfectly.

Any hints / ideas?

---

### Post by ncs_one on 2012-10-11
ok, a friend of mine reminded  me of the existence of nvidia-settings. I enabled the second screen from there and all is good.. :$

---

