---
title: "Black Borders"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by normcross on 2012-04-20
Hi, I'm using 12.04 through HDMI and I was wondering if there is a way to get rid of the large black borders on my screen. My 10.10 installation (on the same machine) shows full screen fine. Graphics via ATI.

Thanks.

---

### Post by ronaldbrijo on 2012-04-21
Hey,

you need to go to the catalyst control panel, under display manager, select the display with the black borders, go to adjustments... move the slider in scaling options to 0%.

This will rid you of the black borders.

---

### Post by normcross on 2012-04-21
Hi,

Thanks for the reply, but I must be going blind. I don't have an adjustments tab or whatever. Just been starring at it for an hour like some demented idiot, clicking everything ten times.

I've got Catalyst Version 12.3 and
Catalyst Control Center Version 2.14, if that's any help.

Cheers.

---

### Post by Smask on 2012-04-21
So AMD still does overscan/underscan on flat panel displays?

If you can't find the setting in Catalyst Control Center, you can still do:
```
xrandr --output HDMI-0 --set underscan off
```Change HDMI-0 to suit your hardware configuration. Run xrandr without any parameters to see where the display is mounted.

Remember, setting display using xrandr isn't permanent, unless you put it into a script that you run during login.  

There's also aticonfig:
```
aticonfig --tv-overscan=off
```If you mess with aticonfig, there is always a chance you'll end up with a black screen that you have to fix in the recovery console.

---

### Post by normcross on 2012-04-22
Unfortunately that doesn't seem to work.

xrandr reports:-

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm

The measurements at the end are correct but obviously the output is smaller.

Looking in aticonfig, I came across this:-

4. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre.

Is this possibly the way I should be going?

Say:- aticonfig --tv-geometry=100x100+0+0 (too scared to try it)

---

### Post by Smask on 2012-04-22
Maybe your card sends the correct signal, but your display botches it.

Have you tried setting another aspect ratio on your TV? Mine has 16:9, Original and Just Scan (plus a bunch of modes we don't need to bother with).

Those set-top makers who thought that they needed to reserve some lines at the top of the screen for some extra information should have been taken around to the back of the barn and shot. We don't want our digital screens be mutilated with legacy crap that originates from times when we had analogue TV sets...

---

### Post by normcross on 2012-04-22
Mine is on 16:9 as usual.

If I deactivate the driver and reboot it opens up into full screen but I don't get any audio and video plays choppy.

Ubuntu 10.10  (still installed on this machine) has no driver activated and has full screen, audio and plays pretty good full screen video. 

The 10:10 driver used to burn up the login screen with weird black line type artifacts. Quite pleasant to watch but not too helpful.

Back to 10.10 to do my video editing...I use every inch of space.

---

