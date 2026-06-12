---
title: "HOWTO: Series 9 Elantech Touchpad Ubuntu 12.10, Mint 14"
date: 2013-02-01
forum: Tutorials
---

### Post by edmondt on 2013-02-01
Finally got it working! Its beautiful I want to cry :)

The 2nd Gen Series 9 13" X3C uses the Elantech Touchpad which has always been incorrectly reconized as a PS/2 Mouse, after a lot of reading I have finally managed to fix by doing the following:

1. Plug in a USB mouse.

2. Remove any /etc/modprobe.d/psmouse.conf, /etc/modprobe.d/psmouse.modprobe stuff you might have done.

3. Install the driver:

```
cd /usr/src/
sudo wget http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2
sudo tar jxvf psmouse-elantech-v6.tar.bz2
sudo dkms add -m psmouse -v elantech-v6
sudo dkms build -m psmouse -v elantech-v6
sudo dkms install -m psmouse -v elantech-v6
```

4. Reboot, move your trackpad around till it the cursor moves.

5. Check your input list:
```
xinput list
```

6 You should now see "ETPS/2 Elantech Touchpad"

Simply install the updated kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

7. synclient -l detects nothing yet, you have to update your kernel:

- Goto: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)
- Download all the deb depending 32 or 64bit:

64bit:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb
```

32bit:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_i386.deb
```

Install them all, update grub and boot into the new kernel, tada! twofinger scrolling and touchbad option is enabled in the mouse setting.

My synclient -l:

```

Parameter settings:
    LeftEdge                = 118
    RightEdge               = 2846
    TopEdge                 = 101
    BottomEdge              = 1771
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 154
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 70
    HorizScrollDelta        = 70
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0570613
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 280
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 6
    LBCornerButton          = 7
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 2
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 5
    PalmMinZ                = 40
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 17
    VertHysteresis          = 17
    ClickPad                = 1
    RightButtonAreaLeft     = 2300
    RightButtonAreaRight    = 2946
    RightButtonAreaTop      = 1040
    RightButtonAreaBottom   = 1872
    MiddleButtonAreaLeft    = 1800
    MiddleButtonAreaRight   = 2299
    MiddleButtonAreaTop     = 1200
    MiddleButtonAreaBottom  = 0


```

My 52-synaptics-custom.conf in /usr/share/X11/xorg.conf.d:

> Section "InputClass"
Identifier      "samsung n900x3c clickpad"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig"     "On"
Option "RTCornerButton" "2" #right-click to bottom right
Option "RBCornerButton" "3" #right-click to bottom right
Option "LTCornerButton" "6" #right-click to bottom right
Option "LBCornerButton" "7" #right-click to bottom right
Option "TapAndDragGesture" "1" #tap&release then tap&drag
Option "PalmDetect" "1" #avoid bad track behavior
Option "VertTwoFingerScroll" "1" #two-finger vertical scroll
Option "VertEdgeScroll" "0" #right edge vertical scroll
Option "TapButton1" "1" #one-finger tap = left-click
Option "TapButton2" "3" #two-finger tap = right-click1
Option "ClickPad=1"
Option "SoftButtonAreas" "2300 0 1200 0 1800 2299 1200 0"
EndSection

Interesting reading:
[http://ubuntuforums.org/showthread.php?p=11770109](http://ubuntuforums.org/showthread.php?p=11770109)

---

### Post by yngvewb on 2013-05-17
Hi! I have the same problem as you with Series 9 and Ubuntu 13.04. I get an error. Do you know what is wrong? 

:/usr/src$ sudo dkms build -m psmouse -v elantech-v6


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
make KERNELRELEASE=3.8.0-21-generic -C /lib/modules/3.8.0-21-generic/build M=/var/lib/dkms/psmouse/elantech-v6/build/src psmouse.ko....(bad exit status: 2)
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
**ImportError: No module named apport**
Error! Bad return status for module build on kernel: 3.8.0-21-generic (x86_64)
Consult /var/lib/dkms/psmouse/elantech-v6/build/make.log for more information.

---

### Post by madko on 2013-05-26
you should install python-apport. But then it will fail to build against kernel 3.8+ since psmouse-elantech-v6/src/synaptics.c is missing one parameter for input_mt_init_slots (line 699). You can edit this line to have:

input_mt_init_slots(dev, 2, 0);

0 is the missing parameter (some flags).

then it should build. 

Not sure if this tutorial is still up to date. I'm on 13.04 and don't want to install older kernel.

---

### Post by beachbum2049 on 2013-05-28
> **madko said:**
> you should install python-apport. But then it will fail to build against kernel 3.8+ since psmouse-elantech-v6/src/synaptics.c is missing one parameter for input_mt_init_slots (line 699). You can edit this line to have:

input_mt_init_slots(dev, 2, 0);

0 is the missing parameter (some flags).

then it should build. 

Not sure if this tutorial is still up to date. I'm on 13.04 and don't want to install older kernel.

I saw this very solution posted in Arch AUR, and it allows the module to build but doesn't give me multitouch (Series 7 NP740U3E), and while it does correctly identify the device as ELan Click Pad ETF1059, but it is still treated as a simple ps/2 mouse. Interestingly, in Windows 8 on my machine, it shows the mouse is connected to a PS/2 port internally.

---

### Post by vik1234 on 2013-06-02
> **edmondt said:**
> 
Install them all, update grub and boot into the new kernel, tada! twofinger scrolling and touchbad option is enabled in the mouse setting.


Can you provide instructions for these setps too?

---

### Post by madko on 2013-06-15
Thanks to Matteo Delfino's patch (cf [https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch](https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch) ) I've been able to make my touchpad to work

```


cd /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7
reboot

```

---

### Post by pepl on 2013-06-15
> **madko said:**
> Thanks to Matteo Delfino's patch (cf [https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch](https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch) ) I've been able to make my touchpad to work

```


cd /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7
reboot

```

Works like a charm with my Samsuns Series 7! Thx a lot to Matteo and Madko!

---

### Post by nikolawannabe on 2013-06-16
I've got the Samsung Series 9.  I applied Matteo Delfino's patch, and it caused the touchpad to recognize correctly in xinput.  And dmesg looks fine as well.  However, my trackpad does not work at all, and synclient -l still indicates no synaptics driver is loaded.*[COLOR=#000000][I]*[/COLOR][/I]*[COLOR=#000000][I]*[/COLOR][/I]

---

### Post by simontaylor on 2013-07-12
Hi, running Mint 13 Maya on an Asus U43JC - intermittent problems with the trackpad, which I've tried previously to solve to no avail. Recently cursor has become extremely jumpy, deleting items, particularly annoyingly in gnote... found this thread and tried to apply these instructions

> d /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget [http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2](http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2) 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7
reboot

response to build:
> Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-49-generic -C /lib/modules/3.2.0-49-generic/build M=/var/lib/dkms/psmouse/elantech-v7/build/src psmouse.ko.....(bad exit status: 2)
ERROR (dkms apport): binary package for psmouse: elantech-v7 not found
Error! Bad return status for module build on kernel: 3.2.0-49-generic (x86_64)
Consult /var/lib/dkms/psmouse/elantech-v7/build/make.log for more information.

response to install is of course the same:

> Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-49-generic -C /lib/modules/3.2.0-49-generic/build M=/var/lib/dkms/psmouse/elantech-v7/build/src psmouse.ko....(bad exit status: 2)
ERROR (dkms apport): binary package for psmouse: elantech-v7 not found
Error! Bad return status for module build on kernel: 3.2.0-49-generic (x86_64)
Consult /var/lib/dkms/psmouse/elantech-v7/build/make.log for more information.


no binary support for elantech-v7 - so no dice.

xinput list:
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=13	[slave  pointer  (2)]


Any help would be greatly appreciated.

Thanks, 
Simon

---

### Post by c.gonzalo.luengo on 2013-11-17
> **madko said:**
> Thanks to Matteo Delfino's patch (cf [https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch](https://launchpadlibrarian.net/142425881/0001-elantech-fix-for-newer-hardware-versions-v7.patch) ) I've been able to make my touchpad to work

```


cd /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7
reboot

```


Thank you very much  to both !!! :lolflag:

---

### Post by Xalabam on 2013-12-08
Windows 8.1 improves the trackpad behavior greatly , ¿ have we got any chance that those new drivers would be adapted to ubuntu ?

at the moment, trackpad at series 9 using ubuntu are very jumpy.

---

### Post by peppezic on 2013-12-10
Hi guys!
I own an ASUS X551CA. I'm running 12.04 lts with kernel 3.5.0-44-generic. 

dmesg shows: 
psmouse serio4: elantech: unknown hardware version, aborting...

xinput list shows:
PS/2 Elantech Touchpad id=12 (slave pointer(2))

So I built version 6 correctly, I rebooted and it was recognized as [COLOR=#000000]ETF1059 (by xinput) [/COLOR]but I was not able to scroll with two finers and, in the settings, I could not even enable multitouch.

So I tried to build elantech-v7 but I get:
ERROR (dkms apport): binary package for psmouse: elantech-v7 not found

Do you have any idea?

---

### Post by Xalabam on 2013-12-12
I just updated to kernel 3.8 and i did install elantech-v7 and for the first time in this computer i am *happy* with the way the trackpad reacts now.

---

### Post by Lula_F on 2014-01-07
Hello!

I have an ASUS X551CA running Mint 16, kernel version 3.11.0-12-generic, and I too have problems with my touchpad (scrolling doesn't work and the touchpad is not properly recognized).

I tried the solution proposed, but when I run
```
sudo dkms build -m psmouse -v elantech-v6
```
I get the following output:
```


Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make  KERNELRELEASE=3.11.0-12-generic -C /lib/modules/3.11.0-12-generic/build  M=/var/lib/dkms/psmouse/elantech-v6/build/src psmouse.ko.....(bad exit  status: 2)
ERROR (dkms apport): binary package for psmouse: elantech-v6 not found
Error! Bad return status for module build on kernel: 3.11.0-12-generic (x86_64)
Consult /var/lib/dkms/psmouse/elantech-v6/build/make.log for more information.
```

Could someone help me through this?

I am also very interested into knowing if peppezic managed to solve the problem, as we have the exact same laptop.

Thank you very much!

---

### Post by Bucky Ball on 2014-01-07
*Thread moved to **Tutorials**.*

---

### Post by aartau on 2014-03-03
[COLOR=#000000]The solution is posted here- [/COLOR][https://bugs.launchpad.net/ubuntu/+s...x/+bug/1166442]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442")[COLOR=#000000][COLOR=#000000] Comment #137.

After you click on the link, make sure you click on "view all ... comments" to load attachments within postings.[/COLOR][/COLOR]

---

