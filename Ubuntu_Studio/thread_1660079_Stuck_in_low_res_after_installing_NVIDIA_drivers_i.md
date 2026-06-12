---
title: "Stuck in low res after installing NVIDIA drivers in U-Studio10.10"
date: 2011-01-04
forum: Ubuntu Studio
---

### Post by Shlomir on 2011-01-04
Hi there,

I upgraded to Ubuntu Studio 10.10 and installed the latest NVIDIA drivers from command line, now I can't get hi-res graphics, when before I had 1600x1050.

My grafix card is NVIDIA FX5700, what are the Xorg.conf changes I need to change?

---

### Post by cchhrriiss121212 on 2011-01-05
Your card requires the 173 series driver, is this the version you used?

Have you checked nvidia-settings? Ubuntu does not need to use an xorg.conf anymore.

---

### Post by wkulecz on 2011-01-05
> **cchhrriiss121212 said:**
> 
Have you checked nvidia-settings? Ubuntu does not need to use an xorg.conf anymore.

So how do you fix it when its screwed up?

I have a 10.04 system that don't work after some upgrades -- did them before shutting down for the holidays and upon my return the system won't boot :(

I could get low resolution graphics by dual booting and replacing my xorg.conf file with the xorg.conf.failsafe that was there, but I still get no mouse or keyboard so system is dead.

If I know what to change I can do it by dual booting but I've no clue as to why the mouse and keyboard are not working :(

---

### Post by realzippy on 2011-01-05
> **cchhrriiss121212 said:**
> Your card requires the 173 series driver, is this the version you used?

Have you checked nvidia-settings? Ubuntu does not need to use an xorg.conf anymore.

...ubuntu **needs** an xorg.conf when running any NVIDIA-driver.

@ Shlomir 

please post your xorg.conf

@ wkulecz

Boot in recovery mode,drop to shell,log in and run:

```
sudo nvidia-xconfig
```

BTW,maybe opening own thread...?

---

### Post by wkulecz on 2011-01-06
Two problems I don't seem to have any recovery mode options on my Grub2 boot menu, and when it does boot to low graphics mode the mouse and keyboard do not work at all.  I need to press the reset/power button to proceed :(

It is not a hardware issue since I can dual boot to 8.04 just fine.  I'm trying to figure out what is not running that keeps the mouse and keyboard from working.

---

### Post by realzippy on 2011-01-06
@ wkulecz

...no recovery mode?Pressed shift?Cannot believe...
Anyway,when dualbooting you could start 8.04 and delete the malicious 10.04 xorg.conf from there...

---

### Post by wkulecz on 2011-01-06
> **realzippy said:**
> @ wkulecz
Anyway,when dualbooting you could start 8.04 and delete the malicious 10.04 xorg.conf from there...

I've already done the xorg.conf thing from 8.04 and get the 10.04 low resolution desktop, but the mouse and keyboard are not working so can't do anything.

I hate all the useless differences grub2 introduced :(  I'll see if holding the shift key down while booting give me extra options.

---

### Post by realzippy on 2011-01-06
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
EndSection


```

..try this xorg.conf

---

### Post by wkulecz on 2011-01-07
I added your mouse and keyboard sections to the xorg.conf file and it made no difference -- still no mouse or keyboard once it boots into low graphics desktop.

---

### Post by realzippy on 2011-01-08
@ wkulecz
Assuming the 173.xx driver is still installed(but not working),I wanted
you to copy the whole file(what should fix your resolution issue also)...
 
Anyway,mouse/keyboard should have worked.
Did you change boot parameters?Disabled nouveau?
Can you post the xorg.conf you use?

---

### Post by WisJim on 2011-01-08
> **realzippy said:**
> @ wkulecz

...no recovery mode?Pressed shift?Cannot believe...
Anyway,when dualbooting you could start 8.04 and delete the malicious 10.04 xorg.conf from there...

I have a similar problem - stuck in low res in Ubuntu.  I run a quad boot system (Vista, UStudio 10.1, CAE 8.04, and Ubuntu 10.1).  All are loaded in their own partitions. Ubuntu is the only one with the low res problem.  I updated my xorg.conf using the settings you suggested with no luck.  

A couple of Questions: 1. If I delete the xorg.conf does it recreate itself during the reboot process?  2. Can I delete it using the command line.  3. With 10.1 running for two systems is there a conflict I need to watch out for?  

Thanks

---

### Post by realzippy on 2011-01-08
> **WisJim said:**
> I have a similar problem - stuck in low res in Ubuntu.  I run a quad boot system (Vista, UStudio 10.1, CAE 8.04, and Ubuntu 10.1).  All are loaded in their own partitions. Ubuntu is the only one with the low res problem.  I updated my xorg.conf using the settings you suggested with no luck.  

A couple of Questions: 1. If I delete the xorg.conf does it recreate itself during the reboot process?  2. Can I delete it using the command line.  3. With 10.1 running for two systems is there a conflict I need to watch out for?  

Thanks

@WisJim
Welcome to the Forum!
Please open a new (own) thread with your problems/questions;
this thread is already napped and OP seems to have gone..
Will answer your questions there,ok?
Thanks..

---

