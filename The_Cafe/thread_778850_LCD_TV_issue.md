---
title: "LCD TV issue"
date: 2008-05-02
forum: The Cafe
---

### Post by BeachBum on 2008-05-02
I need to pick the brain of the tv gurus...

I have a nice LCD TV that I have hooked up to my ubuntu server and to the cable box.  Yesterday I turned on my tv after it being turned off all day and ubuntu has a green tint to it.  I switch to coax input and the color looks fine, and back to PC input (which is VGA) shows ubuntu is still green tinted.  I tried a different cable and it still looked green, and I tried an older LCD monitor and ubuntu's colors looked normal.  Anyone have any ideas as to why the VGA input is looking green?  :confused:

The only thing that has changed in that setup recently is that I installed envy the day before to install the latest and greatest nvidia driver (compiz was a bit slow and jockey was acting strangely).  I installed the driver but didn't reboot until a day later to apply the changes.  Could the new driver be causing this issue?  I'll have a chance to uninstall this evening but wanted some input cause this has me bummed.:(

Thanks for any tips.

---

### Post by ARhere on 2008-05-02
I have never heard of a driver issue that drops an entire color.  What I expect is that your PC connection uses a VGA 15-pin connector and is bent or damaged.  The VGA standard has separate signal pins for the three primary colors.

Check this [wiki ]("http://en.wikipedia.org/wiki/VGA_connector")out and look at your VGA cable and connectors.  If you are seeing a green tint that means your blue or red signal might not be making a good connection (*or their respective grounds*).  More likely to be the red signal, pins 1 & 6.

Check the pins and make sure none of them are bent and also check the female socket for hair and crap.  Most people do not realize that they need to clean out their PC's once in a while.  :)

If the cable is removable, try a new one as well.  To make sure it is not your video card, plug in another monitor to your PC.  If you still see a green tint then it could be your video card.

-AR

---

### Post by BeachBum on 2008-05-02
So I've plugged in a different monitor with a different vga cable, and the different monitor looks fine.  I used my laptop as input with a different vga cable and the lcd tv is still tinted green.  I hit the female connectors with compressed air and everything is still green.  Its weird though, everything has a very slight green tint and the color looks washed out too.  Also, when set to vga input, the on screen OSD's that tell you what connection you're using are not tinted at all, only the actual input its displaying.

DVI, on the other hand, works nicely with my friends macbook pro, but because the DVI input was not designed to work with pc resolutions (says so in the manual), the screen is either too large for the display or too small.  

Any other suggestions for troubleshooting vga?

---

### Post by ZabiGG on 2008-05-02
Hi there ;o)

I'm no expert, but something similar happened to me -- the funny thing about it is the answer was simple:

my hdmi to dvi connector was a tad loose

did you check your connections?

Hope this helps.

---

### Post by BeachBum on 2008-05-02
> **ZabiGG said:**
> Hi there ;o)

I'm no expert, but something similar happened to me -- the funny thing about it is the answer was simple:

my hdmi to dvi connector was a tad loose

did you check your connections?

Hope this helps.

I wish it was that easy, I've been plugging and unplugging various cables today and the picture is still green :(

---

### Post by popch on 2008-05-03
There appears to be a loose connection or damaged wire in the VGA plug/receptable inside the TV.

---

### Post by BeachBum on 2008-05-03
I figure that has to be the case.  It seems someone else on the net has this exact problem but he found no resolution.  In the mean time, I can use DVI but this tv is strange, I can get a beautiful image, but the desktop is off the screen.  I don't understand, though, the monitor claims the resolution is standard 720p (1280x720), nvidia-settings and the screen resolution program say the resolution is 1280x720, but the image is still off the screen.  I think this is called overscan?  Besides guessing and checking custom resolutions to get it to fit, is there a better way to shrink the image in Ubuntu?  (There is no option on the tv to shrink image using DVI).

---

