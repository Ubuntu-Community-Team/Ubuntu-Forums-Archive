---
title: "matrox dual/triple head2go"
date: 2010-06-29
forum: The Cafe
---

### Post by kal stevens on 2010-06-29
I am interested in getting a matrox dual/tripple (Digital/DVI edition) head card.

Has anyone had luck getting it to work with ubuntu?

I think I can get it to operate in the basic way, but I was hoping to get it working in landscape mode.

As 2 side by side monitors.

has anyone had luck doing this?

One thought was that I could configure it in windows and then use it in linux.

Is that part of the configuration stored on the device or in the OS?

Has anyone had luck getting the configuration setup in wine? 

Thanks

---

### Post by Starks on 2010-06-29
Your approach is ***-backwards. Don't even try to brute force a cross-os driver installation or configuration.

I don't know if you need to download a binary driver, but Jockey or the xserver-xorg-video-mga driver should support whatever Matrox card you buy.

---

### Post by kal stevens on 2010-06-29
That is an option but it will not do precisely what I want.
What I want could be done in windows.

Your way (The way I have it working now) ubuntu sees a very long monitor, and then rotates it, so it is a very tall monitor, not 2 monitors side by side.

So for instance if I want to drag a window from one screen to another I drag it down, not side to side.

And I know it is *** backwards, that is why I wanted other options.

---

### Post by kal stevens on 2010-06-29
I realized that you may not be familiar with DualHead2Go

My laptop has one HDMI port, and I wanted 2 external monitors.
Preferably using landscape mode side by side.

DualHead2Go has 1 dvi input (coming from the laptop) and 2 dvi outputs.

So if you hook the dual head up to 2 identical monitors then your computer sees a monitor that is 2x the length.

In windows you can configure it to use landscape/side by side.

Which is why I was asking about wine.

---

### Post by cascade9 on 2010-06-29
WINE wont work...well, I dont think it will work, but you can try it if you want. ;) 

According to matrox, the dualhead2go does have linux support- 

> **Supported Operating Systems**

 Microsoft® Windows® 7, Windows Vista&#8482; (32/64bit), Windows XP (32/64bit), Windows Server 2003/2008 (32/64bit), Windows 2000, Mac® OS X (Leopard/Snow Leopard) 2 and Linux 3
[http://www.matrox.com/graphics/en/products/gxm/dh2go/](http://www.matrox.com/graphics/en/products/gxm/dh2go/)

But seing how they dont have any linux drivers avaible, thats only partially true.

You might be able to hack xorg to make the output (for 2x 1024x768 monitors) 1024x1536, not 2048x768. That should be do-able pretty easy....it would be the rotation that would be the hard bit.

---

