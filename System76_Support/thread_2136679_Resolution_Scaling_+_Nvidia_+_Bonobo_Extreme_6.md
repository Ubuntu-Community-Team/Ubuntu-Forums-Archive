---
title: "Resolution Scaling + Nvidia + Bonobo Extreme 6"
date: 2013-04-18
forum: System76 Support
---

### Post by jaylittle on 2013-04-18
So,

As a proud owner of the bonx6, I have had but one problem with it under Linux that until today I had no resolution for.  I prefer to run my display at a resolution of something less than 1920x1080 as I find that things are too small at this resolution for my taste.  However when it comes to internal laptop displays, the Nvidia drivers don't care to run anything at a resolution less than the native one.  Using metamodes results in the resolution changing, but the Window Manager not resizing correctly so that's a no go as well.

Today I stumbled upon [this site](http://linuxmacbookproretina.blogspot.com/) which provides some details on how somebody solved this problem on a Macbook Pro Retina under Linux.  It makes use of an option available in xrandr that I've never heard of before, the scale option.  He even went so far as to write a little script that makes scaling your display to your preferred resolution really simple.  Of course his script only worked on the MBP.  I have now modified it to work on the bonx6 and thought I would share:
```
#!/bin/bash
#Author:  Travis Gibson
#Modifier: Jay Little
#This script requires an argument for the resolution width
#While originally written to handle resolution scaling on the
#Macbook Pro Retina - I have modified this script to handle
#scaling for the 1920x1080 System76 bonx6 laptop.

if [ -z "$1" ]; then
echo "Usage: Res.sh <resolution_width>";
exit 1;
fi
erg=$( echo "$1")
check=$(xrandr -q | grep LVDS-0 | cut -d " " -f 4 | cut -d "x" -f 1)
if [ "$erg" -eq  "$check" ]; then
echo "The screen is already at this resolution"
exit 1;
fi

resolution=$(xrandr -q | grep LVDS-0 | cut -d " " -f 4);

if [ "$resolution" != "1920x1080+0+0" ]; then
xrandr --output LVDS-0 --scale 1x1;
#Necessary to work around an issue where re-scaling
#only works if the scale is set to 1x1
sleep 3;
fi
scale_w=$(echo "scale=4; $1/1920" | bc; exit );
arg=$(echo "$scale_w""x""$scale_w")
xrandr --output LVDS-0 --scale $arg
sleep 1;
```
This script has been tested using Arch Linux with the latest 319.12 nvidia drivers.  In theory it ought to work everywhere else though.  Please feel free to give it a shot and let me know what you think.  Of course if anybody knows of any trick to switch to a smaller resolution the correct way and force the window manager to resize appropriately, I'm all ears.  But for now, this hack will do the job I think :)

---

