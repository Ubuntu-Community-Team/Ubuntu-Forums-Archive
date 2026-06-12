---
title: "LTSP Dual Screen [virtual] resolution"
date: 2009-04-02
forum: Server Platforms
---

### Post by danielw84 on 2009-04-02
Hi,

I have an Ubuntu 8.10 LTSP server. I have HP t5730 thin clients. The thin client boot through PXe to get there OS. The thin clients can have two screens connected to it. (1 VGA and 1 DVI-D)

I want to use dual head wide. (not mirrored) The only limitation is that the screen resolution can't be higher than 800x600. I want the screens to function on a resolution of 1280x1024.

I have added the option "Virtual 2650 1024" to xorg.conf. When I execute xrandr -q on the server I get:
Screen 0: minimum 320 x 200, current 1280 x 1024, **maximum 2560 x 1024**

When I execute xrandr on a thin client I get:
Screen 0: minimum 320 x 200, current 1280 x 1024, **maximum 1600 x 1600**

The option from xorg.conf doesn't seem to work on the thin client. I have search and search all over to find the correct place to put the "virtual" option, so the thin clients knows it can have a bigger resolution.

Does somebody knows where to put this option so the thin clients also can have a bigger resolution for use with two screens.

I hope somebody can hep me with it, because I am really stuck at the moment.

Thanks for your response.

Daniël

---

### Post by danielw84 on 2009-04-02
At the moment I was about to throw the computer out of the window I found the solution!

Here it is:

Copy xorg.conf to the image filesystem (with the option Virtual specified in it)
sudo cp /etc/X11/xorg.conf to /opt/ltsp/i386/etc/X11

Update image:
sudo ltsp-update-image

Reboot the thin client and is has a bigger virtual resolution for use with multiple screens.

):P

UPDATE:
Thin client hang about an hour working with this solution. So unfortunately it's not the final solution.

---

