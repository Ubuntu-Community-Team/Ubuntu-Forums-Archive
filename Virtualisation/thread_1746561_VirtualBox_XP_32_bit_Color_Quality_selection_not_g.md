---
title: "VirtualBox XP 32 bit Color Quality selection not giving 32bit colour"
date: 2011-05-01
forum: Virtualisation
---

### Post by GROwen on 2011-05-01
Hi all,

My issue is that 32 bit colour depth (which I can set) of my guest OS (XP) doesn't appear to be true 32 bit colour.

I'm running
Host: Ubuntu 11.04
VirtualBox 4.0.6
Guest: XP with all updates installed
Graphics card: GeForce 7600GT 512MB

I  have the system hooked up to a 42" Plasma screen at a resolution of  1024x768 but the image isn't as crisp and clear as I would expect,  basically colour transitions are very rough and nothing looks as crisp  as the host, Ubuntu (11.04).

I have 16MB assigned to the video.

Under  XP Control Panel>Display>Settings I can set the resolution to  800x600, 1024x744 and 1024x768 (a manually added via command line  setting) and the Color Quality to 16, 24 and 32 bit. But even at 32 bit  the color scale looks very pixelated, not a smooth gradient.

Thanks in advance for any help anyone can provide me with this,

---

### Post by lmarmisa on 2011-05-03
Have you installed the VB Guest Additions?:

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by GROwen on 2011-05-03
I have but I'm now thinking that the issue is related to the propriety drivers not being in use.

When I have a look at Additional Drivers I have the latest driver active but a message reads;

> The driver is active but not in use.

So for some reason it appears the nVidia driver isn't being chosen as the priority driver for some reason.

How do I disable the Ubuntu graphics driver so that the nVidia one is in use?

---

