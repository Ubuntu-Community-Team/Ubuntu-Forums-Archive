---
title: "[Lubuntu] Intel Video Drivers in Lubuntu"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mjhatten on 2012-03-22
I am running 12.04 on an Acer Aspire One with an Atom N550 processor.  Would downloading Intel Video Drivers improve my video performance?

---

### Post by snowpine on 2012-03-22
**xserver-xorg-video-intel** is installed by default in L/K/X/Ubuntu. (Intel cards are very popular.) Unless you removed it for some reason?

Tell us more about the video problems you're experiencing? I have generally heard good things about Lubuntu on the Acer netbooks...

---

### Post by mjhatten on 2012-03-22
I'm using the native graphics functions from the Processor. I'm looking at streaming video from HBOGO.COM on Chromium.  It just seem a little jerky.  The network doesn't look stressed when I look at System Monitor -- it looks like the CPU might be getting hammered a little, though.  I was just wondering if downloading the Intel GMA500 package might speed things up a little.

I wouldn't call this a problem -- I'm just trying to optimize what I have.

FWIW:

-Display-
Resolution		: 1024x600 pixels
Vendor		: The X.Org Foundation
Version		: 1.11.3
-Monitors-
Monitor 0		: 1024x600 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor		: Unknown
Renderer		: Unknown
Version		: Unknown
Direct Rendering		: No

---

### Post by mjhatten on 2012-03-22
BTW -- I concur that Lubuntu runs great on my Acer Netbook.  If I had stayed with Windows 7, I would have chucked this computer as a piece of junk.  Now it's actually fun to use.

---

### Post by snowpine on 2012-03-22
If you have the dreaded GMA500 "poulsbo" graphics then yes, you will need to jump through some hoops: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

But I thought GMA500 was z-series Atoms, not your n-series? Can you confirm your graphics chipset with:

```
lspci | grep VGA
```

What format is your streaming content from HBO? If it's Flash format then you're probably out of luck; you'll need at minimum a dedicated graphics card with 128mb according to: [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

For example a dedicated nVidia card would take over the work so the CPU isn't being hammered.

Another solution is to download the video to your hard drive (if possible) and then watch it locally with your favorite movie player, this is what I do on my Asus EEE netbook.

---

### Post by mjhatten on 2012-03-22
No response, just back to the terminal prompt.

---

### Post by mjhatten on 2012-03-22
And it is Flash -- so I guess this is good as it gets.  Thanks.

---

### Post by snowpine on 2012-03-22
Hmmm, maybe Ubuntu is different and you need to:

```
sudo lspci
```

?

---

### Post by snowpine on 2012-03-22
ps Someone on these forums has put together a "Flash Aid" plugin for Firefox that will apply some common Flashs optimizations/hacks. Haven't tried it personally but I've heard good things! :)

---

### Post by mjhatten on 2012-03-22
I got the "command not found" error for lspci.

---

### Post by snowpine on 2012-03-22
Try:

```
/sbin/lspci
```

or:

```
sudo /sbin/lspci
```

---

### Post by mjhatten on 2012-03-22
Same error.

---

### Post by snowpine on 2012-03-22
Make sure you have **pciutils** installed, otherwise I'm stumped. :)

Is another way to verify your graphics chipset, perhaps your owner's documentation or google your model number?

---

### Post by mjhatten on 2012-03-22
Don't know what I did wrong.  It seems to work now.  Looks like I have N-series Integrated Graphics.  I suspect the Lubuntu package is already doing everything it can.


michael@michael-AOD255:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
michael@michael-AOD255:~$

---

