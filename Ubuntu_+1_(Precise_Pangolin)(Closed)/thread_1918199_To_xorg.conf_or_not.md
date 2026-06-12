---
title: "To xorg.conf or not?"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-01-31
ATI RV630 [Radeon HD3600 Series] 3650 to be Precise...

If I do not generate xorg.conf I get:```
Tue Jan 31 19:37:35 CET 2012
Ubuntu precise (development branch)
Linux 3.2.0-2.dmz.1-liquorix-amd64
unity 5.0.0

OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 8.0-devel

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```If I generate xorg.conf I get &#8222;yes&#8220; everywhere.

Xorg-edgers, many other ppa's and all is up to hour...

---

### Post by Harry33 on 2012-02-01
Hmm, I do not have the package mesa-utils installed (only suggested by some x11 packages).
However, I do have /etc/X11/xorg.conf file.
I need it, because of the newest nvidia-current available (295.17) and xserver 1.12 rc2.

---

### Post by zika on 2012-02-01
> **Harry33 said:**
> Hmm, I do not have the package mesa-utils installed (only suggested by some x11 packages).
However, I do have /etc/X11/xorg.conf file.
I need it, because of the newest nvidia-current available (295.17) and xserver 1.12 rc2.
Corrected, mesa-utils are not relevant for this thread...

I've got some spare time and (just) checked (I did not want to speculate since lot of stuff happened lately), the only stuff I need in xorg.conf to make those two &#8222;no&#8220; go to &#8222;yes&#8220; is:
```
Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection
```...

---

### Post by Harry33 on 2012-02-01
So, if you remove the xorg.conf file,
can you still get to Unity Desktop (3D)?

---

### Post by zika on 2012-02-01
> **Harry33 said:**
> So, if you remove the xorg.conf file,
can you still get to Unity Desktop (3D)?
No.
If there is not xorg.conf there is no 3D support...
If there is xorg.conf (with proper lines given above) there is 3D support...

---

### Post by Harry33 on 2012-02-01
> **zika said:**
> No.
If there is not xorg.conf there is no 3D support...
If there is xorg.conf (with proper lines given above) there is 3D support...

Right, that means your graphics card is not recognised properly during booting process.
Might be a kernel issue.

Have you tried  a 3.3 branch kernel?

---

### Post by zika on 2012-02-01
> **Harry33 said:**
> Right, that means your graphics card is not recognised properly during booting process.
Might be a kernel issue.

Have you tried  a 3.3 branch kernel?
I'm on daily for years...

---

### Post by MoreOrLess on 2012-02-01
It might be helpful to post/pastebin your Xorg log from booting without xorg.conf

---

### Post by GuyZerO on 2012-02-01
I Hope i'm not too far off topic...

My computer won't boot with GUI if i have an xorg.conf file i was using CLI for weeks before i figured out that was the problem. once i rm that file it was right back to normal.

My question is what does a normal xorg.conf file look like? I ask because the ones my computer generates all cause failure

---

### Post by zika on 2012-02-02
> **MoreOrLess said:**
> It might be helpful to post/pastebin your Xorg log from booting without xorg.confFrom boot? That would not help. From starting X might. I will get that as soon as I get enough time on my hands to play with that...

---

### Post by zika on 2012-02-03
After upgrade today (among others radeon driver) I get all &#8222;yes&#8220; even without /etc/X11/xorg.conf. Cool!
I'll mark this thread &#8222;solved&#8220; if that status persists for a day... ;)

---

