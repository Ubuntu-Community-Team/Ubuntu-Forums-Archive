---
title: "After Installing Nvidia Drivers screen freezes (shaking)."
date: 2016-05-13
forum: Ubuntu Studio
---

### Post by krishnansrinivasan2 on 2016-05-13
UBUNTUSTUDIO 16.04.
AMD Phoenix II , Nvidia GTx 560 , gigabyte bulldozer support motherboard , 8gb RAM. (5 year old hardware). 320Gb 5400rpm main drive , 500gb 7200RPM spare drive.
After updating from default driver Nouveau driver to Nvidia 361.42 driver.
I lost the splash screens from boot and shutdown.Boot time and shutdown time has increased.
It is not a issue at all.
My screen would freeze shaking with pixelated patches all over the screen. Each time I had no choice but will have to restart.
I saw a youtube video and I updated my xconfig file from nvidia xserver settings app. 
Things turned to normal.
But recently this week , three times the same issue turned up. 
I had to restart once , one time Ubuntustudio popped an error to report quickly after resuming from freeze and shake ,
the last time ubuntustudio logged me out just like that .. and problem seem to be fixed when I logged backin (no restart ).
So far no jittering yet...
I presume this returned since I had my machine on for about 1.5 days each time .
Is their any solution to this.? How to tackle this if it comes back again.?

---

### Post by jejeman on 2016-05-14
I have similar card. Nvidia driver.
I always remove quiet boot to avoid bugs.
I add this to xorg.conf
```
Section "Device"
 Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefaultAC=0x1"
EndSection
```
After that - no power saving, but also no artifacts and freezing. I'm not on 16.04 yet, but this is my workaround for a long time now.

---

