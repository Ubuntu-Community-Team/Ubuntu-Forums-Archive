---
title: "DisplayLink Adapter with Kernel 3.10rc6"
date: 2013-06-18
forum: Ubuntu Development Version
---

### Post by celluloid on 2013-06-18
Hi all,

After MONTHS of attempting various different drivers and tweaks to get a couple of different DisplayLink adapters to work, I've installed Kernel 3.10rc6 and the adapter works pretty much out of the box! :)
I've however found that performance (of my whole system) is severely degraded when using it. Within Windows, these adapters work really well, however the monitor connected via the adapter is somewhat slow (this is likely caused by USB 2.0 bandwidth) - but whilst using Ubuntu with the adapter, my whole system is slow.

The performance is most noticeable with any Unity animations such as opening the launcher or dash :(

I'm really not sure where to start troubleshooting this issue to see if I can make performance better - so far I have;
[LIST]
[*]Disabled all Window animations (min/max)
[*]Changed Unity blur to static
[*]Changed unity Low Graphics Mode
[*]Tried xorg-edgers PPA for some newer X packages
[/LIST]

Does anyone have any ideas on what else might help?

Some output below if it might help;

lsusb:
```

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 138a:0008 Validity Sensors, Inc. VFS300 Fingerprint Reader
Bus 001 Device 005: ID 0c45:6421 Microdia 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 005: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)
Bus 002 Device 006: ID 17e9:0360 DisplayLink
```

dmesg:
```
[    3.707636] usb 2-1.2.4: New USB device found, idVendor=17e9, idProduct=0360
[    3.707642] usb 2-1.2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.707645] usb 2-1.2.4: Product: USB to DVI-17
[    3.707648] usb 2-1.2.4: Manufacturer: DisplayLink
[    3.707650] usb 2-1.2.4: SerialNumber: 433724
```

Relevant parts of Xorg.0.log;
```
[    66.812] (II) LoadModule: "fbdev"
[    66.812] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    66.812] (II) Module fbdev: vendor="X.Org Foundation"
[    66.812]    compiled for 1.12.99.902, module version = 0.4.3
[    66.812]    Module class: X.Org Video Driver
[    66.812]    ABI class: X.Org Video Driver, version 13.0
--
--
[    67.185] (II) modesetting(G0): Printing probed modes for output DVI-0
[    67.185] (II) modesetting(G0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    67.185] (II) modesetting(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    67.185] (II) modesetting(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    67.185] (II) modesetting(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    67.185] (II) modesetting(G0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    67.185] (II) modesetting(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    67.185] (II) modesetting(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    67.185] (II) modesetting(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    67.185] (II) modesetting(G0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    67.185] (II) modesetting(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    67.185] (II) modesetting(G0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    67.185] (II) modesetting(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    67.185] (II) modesetting(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    67.185] (II) modesetting(G0): Output DVI-0 connected
[    67.186] (II) modesetting(G0): Using exact sizes for initial modes
[    67.186] (II) modesetting(G0): Output DVI-0 using initial mode 1920x1080
[    67.186] (II) modesetting(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    67.186] (==) modesetting(G0): DPI set to (96, 96)


```

---

### Post by celluloid on 2013-06-19
I've determined that this is fairly specific to Unity (or I guess any DE that uses some hardware acceleration) - if I install MATE or Xubuntu Desktops, my whole session is fast.
The monitor that's driven off the DisplayLink adapter is still a little "jerky" but that's to be expected.

Now that Unity 2D is no longer available, what are my options? I really don't like MATE or XFCE and I'm so used to the Unity workflow.

---

### Post by dino99 on 2013-06-19
> **celluloid said:**
> 

Now that Unity 2D is no longer available, what are my options? I really don't like MATE or XFCE and I'm so used to the Unity workflow.

Gnome-shell is also very close

---

### Post by celluloid on 2013-06-19
Alright, well I settled on KDE - where it's all nice and responsive :)

---

### Post by celluloid on 2013-06-30
> **dino99 said:**
> Gnome-shell is also very close

Unfortunately Gnome-shell was even slower than Unity for me :(

---

### Post by jaws222 on 2013-07-10
> **celluloid said:**
> Unfortunately Gnome-shell was even slower than Unity for me :(


Celluloid, I am having the same issue on my Linux Mint 15 Cinnamon install after upgrading to the 3.10 kernel.  it actually broke my Nvidia, but I installed the Noveau driver and everything works great with dual monitors like before, but when I add the 3rd monitor via Displaylink I see all 3 monitors, but like you get degraded performance.  I tried a few lightweight DE like Razor-QT, XFCE and even Openbox, but no luck.  i think part of my problem is the size of my Displaylink monitor, which is a 37 inch TV and my dual DVI monitors are two identical 19 inch Samsung monitors, but like you they all run fine under Windows.  There's supposed to be a fix coming for the Nvidia under the 3.10 kernel so maybe that will help, but until then I'll just run dual monitors.  Any suggestions?? Have you gotten any better results with your setup recently?

---

### Post by dino99 on 2013-07-10
maybe you can test with lower dpi; check the maximum definition the graphic card can handle
[http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi](http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi)

---

### Post by fyfe54 on 2013-07-10
The 3.10 final kernel has been available since June 30.  Would that help?
It has been working just fine here.

---

### Post by dino99 on 2013-07-10
> **fyfe54 said:**
> The 3.10 final kernel has been available since June 30.  Would that help?
It has been working just fine here.

Thanks for the heads up :D but everyone here is using the bleeding edge stuff  :p
(dont be disturbed by the oldish title ;) )

---

### Post by fyfe54 on 2013-07-10
> **dino99 said:**
> Thanks for the heads up :D but everyone here is using the bleeding edge stuff  :p
(dont be disturbed by the oldish title ;) )

Silly me.

---

### Post by celluloid on 2013-07-11
> **jaws222 said:**
> Celluloid, I am having the same issue on my Linux Mint 15 Cinnamon install after upgrading to the 3.10 kernel.  it actually broke my Nvidia, but I installed the Noveau driver and everything works great with dual monitors like before, but when I add the 3rd monitor via Displaylink I see all 3 monitors, but like you get degraded performance.  I tried a few lightweight DE like Razor-QT, XFCE and even Openbox, but no luck.  i think part of my problem is the size of my Displaylink monitor, which is a 37 inch TV and my dual DVI monitors are two identical 19 inch Samsung monitors, but like you they all run fine under Windows.  There's supposed to be a fix coming for the Nvidia under the 3.10 kernel so maybe that will help, but until then I'll just run dual monitors.  Any suggestions?? Have you gotten any better results with your setup recently?

I used the 3.10 final kernel which was a LITTLE better - but I could only get "decent" performance with KDE 4.10 (went so far as to install Kubuntu) with basically ALL effects turned off.
Eventually, I just got tired of it and missed my Unity workflow too much so I've gone back to just 1x external monitor via VGA on my laptop. 

Ultimately, I'd LOVE to go back to a 3rd monitor via DisplayLink, but we're not quite at a usable state yet. :(

---

### Post by jaws222 on 2013-07-11
> **celluloid said:**
> I used the 3.10 final kernel which was a LITTLE better - but I could only get "decent" performance with KDE 4.10 (went so far as to install Kubuntu) with basically ALL effects turned off.
Eventually, I just got tired of it and missed my Unity workflow too much so I've gone back to just 1x external monitor via VGA on my laptop. 

Ultimately, I'd LOVE to go back to a 3rd monitor via DisplayLink, but we're not quite at a usable state yet. :(


Yeah, I feel the same way with my Cinnamon setup.  Oh well, maybe they'll work out the bugs.

---

### Post by wM6lYlji on 2013-11-02
[QUOTE=celluloid;12697090]Hi all,

After MONTHS of attempting various different drivers and tweaks to get a couple of different DisplayLink adapters to work, I've installed Kernel 3.10rc6 and the adapter works pretty much out of the box! :)
I've however found that performance (of my whole system) is severely degraded when using it. Within Windows, these adapters work really well, however the monitor connected via the adapter is somewhat slow (this is likely caused by USB 2.0 bandwidth) - but whilst using Ubuntu with the adapter, my whole system is slow.
[/CODE]

What for an Adapter are you using? Where can you configure the Display? With 12.04 LTS (kernel 3.10) my screen turns on, but not more....

---

### Post by oldos2er on 2013-11-02
Questions regarding 12.04 should be posted in the support areas of the forum. Ubuntu +1 is for the latest pre-release (in this case 14.04).

Closed.

---

