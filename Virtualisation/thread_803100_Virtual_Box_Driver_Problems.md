---
title: "Virtual Box Driver Problems"
date: 2008-05-22
forum: Virtualisation
---

### Post by handsomeDave on 2008-05-22
I just installed virtualbox and XP. The Host is 7.10 and the Guest is Windows XP. I'm having a problem with the audio, if virtualbox is running I get audio from xp, but not ubuntu. I get audio from the host if virtualbox isn't running.
Also I'm trying to figure out if there's anyway that I can get XP to recognize the video card, Radeon X1900XT. The main reason that I wanted to get XP running is to play games. And games won't play because whatever video driver is in XP now, won't support dx9 or OpenGL.

If anybody's got answers to either of these problems, it would be greatly appreciated.

I'm running a 
Pentium D at 3.2Ghz
2GB Ram
Ati Radeon X1900XT

Thanks,
Dave

---

### Post by Skeet on 2008-05-22
Thats fairly common.

Are you using some form of USB Audio? Only one os is able to utilise the sound drivers at once. It has to take 100% control of the drivers to be able to function, so only one OS will have sound at one time.

As per your graphics question. Virtualbox doesn't support DX9 or OpenGL natively. There is however VMWare Workstation 6.5 (currently in beta stage) which has support for DX9 and OpenGL. You might want to wait for that or run your games in Wine, because there are no current Virtual Managers that support them.

---

### Post by handsomeDave on 2008-05-22
No I'm just using the audio on the mobo.
I guess that your answer would explain why I haven't been able to find anything to help yet.

Thanks.

---

