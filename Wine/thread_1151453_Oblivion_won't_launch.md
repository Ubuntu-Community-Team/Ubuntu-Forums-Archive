---
title: "Oblivion won't launch"
date: 2009-05-06
forum: Wine
---

### Post by runaway on 2009-05-06
Hey all, I setup the latest version of wine to play Oblivion on but I'm having a bit of trouble. Whenever I try to play it, it just flashes a black screen (fullscreen) then nothing happens and I'm back to the desktop. When I run it in the terminal (wine Oblivion.exe) it has no output at all and just flashes and brings me back to the command line where I can type stuff. I installed DX9 with winetricks and that might have done something, I'm not sure.

I'm running the latest version of Ubuntu (Jaunty) 64bit edition.
ATI Radeon HD 4850 video card.
AMD x2 64 6000+ 3Ghz cpu.

Help would be awesome! I've finally taken the lunge and totally deleted windows off of my hard drive and seeing as how this is one of the few games I play it would be nice to get it to work! :)

---

### Post by asdfoo on 2009-05-07
> **runaway said:**
> Hey all, I setup the latest version of wine to play Oblivion on but I'm having a bit of trouble. Whenever I try to play it, it just flashes a black screen (fullscreen) then nothing happens and I'm back to the desktop. When I run it in the terminal (wine Oblivion.exe) it has no output at all and just flashes and brings me back to the command line where I can type stuff. I installed DX9 with winetricks and that might have done something, I'm not sure.

I'm running the latest version of Ubuntu (Jaunty) 64bit edition.
ATI Radeon HD 4850 video card.
AMD x2 64 6000+ 3Ghz cpu.

Help would be awesome! I've finally taken the lunge and totally deleted windows off of my hard drive and seeing as how this is one of the few games I play it would be nice to get it to work! :)

Hello

First of all, ATI is known to have issues in general with Wine, but let's hope that situation improves in the future.

Upgrade to the latest beta release of Wine [http://winehq.org/download](http://winehq.org/download)

If it still doesn't work...

Have you tried setting OffscreenRenderingMode to fbo?  open regedit, HKLM, Software, Wine, Direct3D (create this key), create a new string entry called OffscreenRenderingMode and set the value to fbo.

---

### Post by runaway on 2009-05-07
Thank you for your reply. Yes I have it set to fbo, as well as a few other things tweaked. I will try upgrading to the beta version and get back to you. What really bugs me about this is that the terminal has no output, makes it really hard to find out what the problem is lol.

---

### Post by runaway on 2009-05-07
Well it's fixed now apparently. All I needed was a restart LOL. Now if I could just work out the performance issues hehe.

---

