---
title: "xrandr does not &quot;connect&quot; to intel i915 HDMI output"
date: 2016-02-19
forum: Ubuntu Development Version
---

### Post by gernot4 on 2016-02-19
Hi there,
right now i'm using ubuntu 16.04 with an additional KDE plasma5 dektop
on a Pansonic FZ-g1 toughpad with an external gechic hdmi touchscreen
```
lspci -ks 0:02 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Matsushita Electric Industrial Co., Ltd. 3rd Gen Core processor Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
```

xrandr or sure also arandr does not show my hdmi port as connected
```
xrandr
Screen 0: minimum 8 x 8, current 3840 x 1200, maximum 32767 x 32767
eDP1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1200     60.00*+  59.95  
.......
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected 1920x1200+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1200     60.00* 
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

but i managed to trick x with following lines and the touchscreen shows with black background, but works pretty well as dual monitor now
```
xrandr --addmode HDMI1 "1920x1200"
xrandr --output HDMI1 --mode "1920x1200" --right-of eDP1
```

my problem is that the touch calibration does not seem to work for two displays if x just knows one as connected ?
so i do the following to map the internal display to the internal touch
```
xinput map-to-output 15 eDP1
```
Ok, that works and the internal touchscreen is quite precise now.
But doing this with the not connected hdmi touchscreen gives following error
```
xinput map-to-output 20 HDMI1
Unable to find output 'HDMI1'. Output may not be connected.
```

that makes the external touchscreen unusable cause it makes the curser jump to the internal display, or anyway in some random way, but not where i actually touch

so i think the solution with forcing x to display the second monitor to show is not the solution, cause it's neither "design integrated" in unity or plasma nor arandr and other graphical convenient tool recognize the second display.

i tried the following unit not
FIRST:
added following grub bootoption
```
i915.modeset=1
```
SECOND:
installed intel driver with a tricking ubuntu 16.04 to be 15.10
[https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0)
THIRD:
added following xorg.conf (not knowing if xorg.conf is even used anymore)
```
Section "Device"
    Identifier "card0"
    Driver "intel"
    VendorName  "Intel Corporation"
    BoardName   "Intel Corporation N10 Family Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
    Option      "SwapbuffersWait"    "false"
EndSection
```

any ideas either getting x to connect to the hdmi port or to "force" mapping the touchscreen to the hdmi output by something like "xinput map-to-output 20 HDMI1" ?

thanks in advance

gernot

---

### Post by howefield on 2016-02-19
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by dino99 on 2016-02-19
hdmi is still a problem in many cases; there are better chances when using latest kernel + latest drm + latest graphic driver.

---

### Post by gernot4 on 2016-02-19
I mean i use 16.04, the newest driver i could get from intels site
How "later" could i go ?

---

### Post by dino99 on 2016-02-19
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=xenial](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=xenial)
[https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging/+packages](https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging/+packages)
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=xenial)

in case you get some breakages, use ppa-purge to downgrade to genuine package

---

