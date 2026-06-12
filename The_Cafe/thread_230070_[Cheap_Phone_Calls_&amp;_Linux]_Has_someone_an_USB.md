---
title: "[Cheap Phone Calls &amp; Linux] Has someone an USB phone for SKYPE ?"
date: 2006-08-05
forum: The Cafe
---

### Post by patrick295767 on 2006-08-05
Has someone an USB phone for SKYPE ?

[http://accessories.skype.com/section?SID=2c30bf45f063137e59df01030f796bf3423:4515&secid=38893](http://accessories.skype.com/section?SID=2c30bf45f063137e59df01030f796bf3423:4515&secid=38893)
  
Is it workign these USB hardwares phones for Skype (drivers?) ?

Thx for the nfo !

---

### Post by sitedesign on 2006-08-05
It looks like they just work.

[http://www.pixmania.com/ie/uk/235287/art/a-link/ipu1-skype-usb-telephone.html](http://www.pixmania.com/ie/uk/235287/art/a-link/ipu1-skype-usb-telephone.html)

No drivers needed. May need to tell Skype to use /dev/dsp2 though.

Look at this link as well:
[http://forum.skype.com/viewtopic.php?t=38469](http://forum.skype.com/viewtopic.php?t=38469)

Hope that helps. I think I may buy one now myself since they are so cheap now.

---

### Post by Barney on 2006-09-07
Dapper-Skype working – don't ask me why, it just works (mucho trial & error)
Dual-Boot WinXP Pro<->Dapper; Dell Dimension 3000, 512MB RAM
USB Phone from Skype (Simplyphone/Yealink 1025)

Skype 1.3.0.37
Skype/Tools/Options/Sound Devices 
Audio system to use: Select OSS
Sound Devices
Calls: Select /dev/dsp1
Ringing  Select /dev/dsp1
SAVE

Double click-on Audio icon in the panel, ”Volume Control” window opens; Select File/
Change Device/pick #2 “Analog Devices AD 1980  (OSS Mixer); then
Capture – volume max; speaker clear/mic-redX
Line-in – volume max; speaker clear/mic-redX
Microphone – volume max; speaker clear/mic-redX
CD - volume max; speaker clear/mic-redX
Phone-in - volume max; speaker clear/mic-redX
Phone-out - volume max; speaker clear/mic-clear

The above Volume Control settings may need some small changes, but it's working; I'll experiment more later.

Have been able to make a call while watching/listening to youtube.

---

### Post by jason.b.c on 2006-09-07
Why bother buying one when you can make one...
[http://www.grynx.com/index.php/projects/build-your-own-chat-cord/3/]("http://www.grynx.com/index.php/projects/build-your-own-chat-cord/3/")
:D

---

### Post by patrick295767 on 2006-11-12
Finally, I bought a USB VOIP mobile. ~30$
WIth the new ALSA Skype beta 1.3, it works very fine. 
No drivers, just plug and talk ;)

---

