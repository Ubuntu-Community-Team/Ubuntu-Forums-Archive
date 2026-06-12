---
title: "fallout3 no music bug"
date: 2010-12-27
forum: Wine
---

### Post by Arthur Millar on 2010-12-27
hello

i have been trying to configure wine for fallout 3 using playonlinux with wine prefix 1.1.37 to 1.3.10 to try and fix my no background sound bug 
i have followed a few appdb posts eg pasting the winmm.dll.so into my prefix and adding quartz.dll

i found a patch [here ]("http://bugs.winehq.org/attachment.cgi?id=31242&action=edit") that supposedly fixes the issue but i have no idea how to implement it 
i did post to playonlinux this early this morning but no one replies  
i am using Ubuntu 10.10 and POL 3.8.8
my wine config is using the alsa driver 
and im using the proprietary ati driver for my HD3850
any kind of reply would be nice 
thanks

---

### Post by Arthur Millar on 2010-12-28
bump

---

### Post by antikhrist on 2011-01-07
i seem to have this problem too i have tried adding the winmm.dll.so to the wine folder in both wine and playonlinux im also on maverick too  (x64)

there was indication on another site that it may be an issue with the new kernel i will be trying again on my ubuntu 9.04 (x32) box to see if it works on there 

do you get no sound at all? i try to start the game and have opening clicks and opening video with sound then when the doctor should be speaking nothing at all

---

### Post by antikhrist on 2011-01-09
didnt try the other pc in the end but managed to get borderlands working with pulseaudio and no sound cut out by using 

```
padsp winecfg
``` and setting audio to OSS from what i can tell padsp creates a kinda virtual driver or something between oss and pulseaudio 

it didnt realy help with fallout but it seems to be a step in the right direction might be due to using playonlinux and a diffrent verion of wine  so ill see if applying it to that works im pretty sure that the big issue with fallout is its lack of cooperation with pulseaudio since it aparently works well with winepulse (not that id know with the repositry being down since i started trying) 

also tried disabling winepulse and letting it use alsa but that didnt go down well and seriously messed with a lot of stuff like my bluetooth headset its certainly dug in deep in the GUI

---

### Post by antikhrist on 2011-01-10
i just got sound in fallout3 working :D

i used ```
padsp playonlinux
``` then configured wine for the game by right clicking the game from the menu and selecting configure wine and switching to the OSS driver i now have full sound where i only had the clicks and bits of video sound 

give it a try see if it helps with yours

---

