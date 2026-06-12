---
title: "Dual Display Broken"
date: 2016-03-21
forum: Ubuntu Development Version
---

### Post by cyanideandfibergla on 2016-03-21
Hey all! I've been trying to settle on a flavor of ubuntu and I've been running Mate 16.04. I'm guessing it's because this is a beta version, but I haven't been able to get any of the outputs on my GPU to work, only my motherboard, rendering my dual display setup useless.
1) LSPCI recognizes the card (750ti)
2) I am running proprietary drivers
3) Scanning for the second display does nothing
4) Both displays work when booting from Windows
5) Naturally, this is a brand new install and it is fully up-to-date.

So I'm not really sure where to go from here. If anyone could help me out, it'd be much appreciated.

---

### Post by X-RED_Tech on 2016-03-21
What version of those proprietary drivers are you using?

---

### Post by cyanideandfibergla on 2016-03-21
Currently I'm running 340.96. I was previously running 361.28 and I think this also happened with Nouveau, but I wasn't using that for very long at all.

---

### Post by X-RED_Tech on 2016-03-21
361.28 is the recommended one.

---

### Post by cyanideandfibergla on 2016-03-22
Okay, well, after switching to 361.28, I can confirm that this behavior hasn't gone away. I think this is somehow related to bbswitch, which shows "NO DISCRETE VGA FOUND" during bootup.

---

### Post by sandyd on 2016-03-22
Hi, are both of the displays plugged into the card, or is one plugged into the motherboard and one using the card?

Could you post the output of
```

xrandr
```

---

### Post by cyanideandfibergla on 2016-03-22
This is the boot message displayed, the bbswitch one was different. NO ACPI VIDEO BUS FOUND
Here is my xrandr output:
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    60.00  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

X server is configured to use Nvidia if that has any meaning. Also, only displays plugged into the motherboard work. Anything connected to the GPU is a no go, but only in Linux. One is on the card, the other on the board. This has long been a windows setup and these monitors work fine there.

---

### Post by X-RED_Tech on 2016-03-23
Motherboard? Because... By default in many desktops you cannot use both integrated and discrete graphics, it's one or the other (BIOS defined). Somehow in Windows sometimes it's possible to work around this limitation but not in Linux.

---

### Post by cyanideandfibergla on 2016-03-23
While it's true that this isn't normally possible, my BIOS-defined setting automatically activates both graphics processors. (For reference, that's the Windows workaround. I don't believe there's any other way to do it.) Linux appears to recognize both, but fails to use one. Drivers for the discrete graphics are running and some of the system software, such as lspci, recognizes it. Strangely, even though that's true, the system renders with my integrated graphics and doesn't offer drivers and such. I'm not sue off the top of my head if the integrated card is even recognized properly by the system. I will change my BIOS setting to use the discrete card exclusively and post my results. 

I have a feeling I'm gonna drop about $30 on cabling just to get this working -_-

Edit: With or without the integrated GPU running in the BIOS, my 750 is giving me no visuals whatsoever on Linux. Tested on windows and the expected results, one monitor working, occurred. Gonna try at earlier version for lack of better ideas.

---

### Post by howefield on 2016-03-24
Moved to the "*Ubuntu Development Version*" forum.

---

