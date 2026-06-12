---
title: "Warcraft 3 - Low FPS, High load times"
date: 2010-07-14
forum: Wine
---

### Post by SkeletalCarp on 2010-07-14
Hi

Sorry if you are reading this question again for the millionth time, I know it's been posted many times before, but I can't seem to find the answer.

_The problems:_
1. Low FPS. Using DotA (popular wc3 map) as an example, I'm getting 15-25 FPS on ubuntu, where I always had 65+ on Win XP.
2. High load times. DotA takes 50 seconds to load, where on Win XP it never took more than 7.

_My system:_
OS: Ubuntu 9.10 Karmic
CPU: Core2Duo E7400
MB: Gigabyte G31M-ES2C
Graphics: Onboard, Intel Graphics Media Accelerator 3100
Wine Version: wine-1.2-rc6

I haven't installed any new drivers, my motherboard doesn't seem to have linux drivers.

I'm already running it with the -opengl switch.

Changing graphics options has made no difference.

Changing resolution to anything other than the desktop resolution results in upside down display and a huge drop in FPS.

Lastly, I'm very new to Ubuntu, so please explain it so that a Windows user can understand.

Thanks!

---

### Post by 98174 on 2010-07-20
You can try editing the registry that Warcraft III is in.
```
wine regedit
```
Navigate to HKEY_Current_User/Software/Blizzard Entertainment/Warcraft III/Video

There should be a dword named 'lockfb'.  Set it equal to 0.  This should increase your fps by a bit.

Also as a heads up, you can change your resolution here as well by modifying 'resheight' and 'reswidth'.  Be sure that you're in decimal not hex when changing these.

Alternatively, you may want to install PlayOnLinux.  It has a patched version of wine (wine1.2-W3-rc3) that fixes bugs in the campaign and Bnet, among other things.   It should automatically prompt you for this when you install wc3 through it.

---

### Post by gufide on 2010-07-20
You can try to make a luncher with (exemple) "wine "/home/guillaume/.wine/dosdevices/c:/games/Warcraft III/war3.exe" -opengl" don't forget, the "-opengl" is the key to solve it

---

### Post by Yaspoon on 2010-07-20
What kind of graphics card do you have?
Nvidia,Intel or Ati?
Do you have the driver for this installed?

---

