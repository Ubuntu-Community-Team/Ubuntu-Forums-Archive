---
title: "ATI catalyst 8.4 is released"
date: 2008-04-16
forum: The Cafe
---

### Post by olskar on 2008-04-16
Hi!
Today the 8.4 drivers were released.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html)

Resolved issues includes:
> # Selecting Wait for vertical retrace in the AMD Catalyst Control Center - Linux Edition no longer results in the FPS of the application not matching the display's vertical refresh rate
# A black screen is no longer observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used. Further details can be found in topic number 737-30687
# Video Playback is no longer displays incorrect colors and additional shadow images when cropping or expanding a video file using a video player that utilizes the XVideo extension 

---

### Post by Mazza558 on 2008-04-16
Right, so they fixed 3 things?! Is that all? 

What about:

-Using 3D apps and Compiz (e.g run more than one 3D program at a time)
-Fixing 2d rendering, like scrolling 
-Making things as fast as they were in Gutsy

---

### Post by mech7 on 2008-04-16
yeah only 3 things seems little... a well atleast they bring out a new driver every month

---

### Post by Saint Angeles on 2008-04-16
i guess i'll be trying this driver when i get home tonight.

but if it sux, i'm gonna be mad.

---

### Post by Polygon on 2008-04-16
> **Mazza558 said:**
> Right, so they fixed 3 things?! Is that all? 

What about:

-Using 3D apps and Compiz (e.g run more than one 3D program at a time)
-Fixing 2d rendering, like scrolling 
-Making things as fast as they were in Gutsy

its most likely 1 or two guys working on their linux driver, vs how many others working on the windows one...be glad that they at least release them at the same time 

I will download/try this with windows/linux when i get home ;)

---

### Post by Teg_Navanis on 2008-04-16
Phoronix believes that a major release (feature-wise) is coming soon:

[http://www.phoronix.com/scan.php?page=article&item=catalyst_84&num=1]("http://www.phoronix.com/scan.php?page=article&item=catalyst_84&num=1")

---

### Post by olskar on 2008-04-16
Hm, wonder what this means?

> This release of the ATI Catalyst™ Linux driver introduces early look support for Ubuntu 8.04 which is also known as Hardy Heron.

---

### Post by Polygon on 2008-04-17
this driver version doesnt work for me on linux. I uninstalled the old drivers using driver manager, then ran ./atiwhatever --buildpkg Ubuntu/hardy

installed the debs using dpkg -i *.deb

and when i restarted i didnt have acceleration....Everything installed fine....didnt give me any errors...

EDIT;

from the phoronix article, this seems to be whats happening to me:

he Catalyst 8.4 changes just include packaging script updates, a few obscure bug-fixes, and an aticonfig fix. With Catalyst 8.4+, aticonfig will no longer crash on newer Linux distributions where there is no device section within the xorg.conf configuration file. This fix means running aticonfig --initial on Ubuntu 8.04 will no longer result in this ATI utility crashing. The official fixes include an AMDCCCLE vertical retrace fix, black screen when switching to the console, and incorrect colors and other issues when using the X-Video extension.

i ran aticonfig --initial and it gave me some weird error about no device section. Maybe im doing something wrong...*goes to check*

---

