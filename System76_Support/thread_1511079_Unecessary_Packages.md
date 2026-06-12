---
title: "Unecessary Packages?"
date: 2010-06-16
forum: System76 Support
---

### Post by Bluebearbevis on 2010-06-16
Good morning all,

6 weeks now with the Lynx and after enabling proposed and backports, she purrs like a kitten.  A couple questions though.  Should I leave these enabled?  I kind of like the idea that I'm a pioneer charting new waters.  Also, I have a panp6 with an nVidia G 105 M, yet I'm finding some ATI stuff installed, see image.  Hmm, I guess I'm not quite sure how to do that yet, so to details.  There are 6 total and 4 start with xserver-xorg-video-then in order, ati, radeon, mach64, and r128.  One is called simply radeontools, and the last is fglrx-modaliases.  I'm thinking I don't need these?  I do have X Updates enabled through Ubuntu tweak, so they might have come from there.  Anyway, on a side note, thanks for the stickers when I stopped by the other day Tom, it was nice to meet the man behind the machine, so to speak.

Thanks,

Richard

---

### Post by isantop on 2010-06-16
You can leave the Proposed/Backports on if you like. You shouldn't end damaging your system if you do.

You should probably leave them on your system. They don't appear to be causing any problems,they they may end up removing Xorg, which is bad. To check, you can run:
```
sudo apt-get autoremove
```
from a terminal (Applications > Accessories > Terminal). This command will automatically check for any packages you don't need and remove them. I usually don't use it unless I get cramped for disk space, which thankfully hasn't happened in a long time.

---

### Post by Bluebearbevis on 2010-06-16
Thanks Isantop,

After reading..., building..., reading..., I received a 4 zero report.  All must be well.  Computer Janitor also says nothing to clean, alas however, as I am still curious.  I don't, that I know about anyway, have any ATI components, so why would I need what appear to be exclusively ATI packages?
Have a good evening!

---

### Post by JohnnyC35 on 2010-06-16
I saw the radeontools in Nvidia system too. I removed them with no ill effects. I just basically go thru a little at a time and remove bits and pieces that I don't think I need, reboot. If all's good and I haven't killed anything then continue removing other stuff. Would be nice if Synaptic had a --no-install-recommends option in it. But then again it shows what it is going to install before hand and you can usually trim it from that.

---

### Post by isantop on 2010-06-17
Because they are so common and relatively small, and required for the open source drivers distributed with Ubuntu, the utilities for both chipsets are included in the Standard Ubuntu Installation, as that you don't have to download a graphics card specific version of Ubuntu.

Actually, I have a few Nvidia utilities on my ATI system. 

Plus, you can probably remove them safely, but keep in mind that they may get downloaded again due to them being a dependency of other packages. 

The general rule in Ubuntu is: if you didn't install it, and apt-get autoremove doesn't remove it, you probably shouldn't remove it either.

---

### Post by Bluebearbevis on 2010-06-17
Thanks for the sound advice both,

I went to Synaptic and the radeontools has no dependencies, so safe to remove.  However, the other ones wanted to remove xserver-...-all too which I didn't think was a good idea.  Then I got to noticing drivers for a bunch of different graphics cards as you mentioned Isantop.  The adage "If it ain't broke, don't fix it," comes to mind.

Again,

Richard

---

### Post by JohnnyC35 on 2010-06-17
heh
if it ain't broke, you're not trying hard enough :P

---

### Post by marshmallow1304 on 2010-06-18
> **Bluebearbevis said:**
> xserver-...-all too which I didn't think was a good idea.

Actually, xserver-xorg-video-all is a meta package, meaning that its only purpose is to depend on other packages to group them together for easy installation.  It can be safely removed.

---

### Post by Bluebearbevis on 2010-06-20
O,

Thanks for the info,
marshmallow...I don't know 
if I'll leave well enough alone,
or remove them all!
As it now seems safe to do so.

R

P.S.  I know, I know, real low,
but it was the best I could do at the time.

---

