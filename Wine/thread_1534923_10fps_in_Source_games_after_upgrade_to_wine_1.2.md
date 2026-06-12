---
title: "10fps in Source games after upgrade to wine 1.2"
date: 2010-07-20
forum: Wine
---

### Post by Yaspoon on 2010-07-20
Hello everyone
After upgrading to the newest wine 1.2 I now get 10 fps in all source based games it starts at 230+ fps then within seconds drops to a stable 10 fps constant I don't know what has happened between wine1.2 rc4 and this. DOes any one have any explanation or ideas? I have deleted ~/.wine to refresh all my files then reinstall directx 9 and vcrun 2005 and a so on and it hasn't helped I also already have the latest nvidia driver from nvidia,org.
Any ideas is much appreciated :)
Thanks Yaspoon

Also while im here wine 1.2 is suppose to support running 64bit applications in 64bit prefixes I have been trying for the last few days to do this how do you do this? 

ubuntu 10.04
Intel Quad core Q6600
Nvidia 8800gts G92 512mb driver @ 256.35

---

### Post by proteusmoteus on 2010-07-20
Installing directx9 is bad for wine. As a rule with wine only install windows libraries necessary to make the game run. The appdb might tell you some dlls are necessary to make the game run but that info gets old fast. Especially with a new major version of wine it is probably better (performance wise) to assume that none of those tricks are still necessary.

Never ever install all of directx9 as that ensures you get no video card hardware acceleration.

---

### Post by asdfoo on 2010-07-20
I know there has been a major update by Valve for CS:S, this could be related.

---

