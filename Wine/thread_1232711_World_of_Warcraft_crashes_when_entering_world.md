---
title: "World of Warcraft crashes when entering world"
date: 2009-08-05
forum: Wine
---

### Post by Killer Mangos on 2009-08-05
Hello!

I recently had my computer reformatted by my father's ex-employee (so I can't use him for help) and he decided to put Ubuntu on it.  I've been having a real struggle trying to get WoW to work.  I've looked through endless forums, google, how-tos, and such and tinkered with a few things.  I've managed to get the background and icons to show, that's all. 

**Problem: **When I enter the world, the game immediately crashes and my monitor goes into sleep mode?  Sometimes, it'll blink before it goes into sleep mode.

[B](Helpful?) information:
[/B]Ubuntu 9.04 Jaunty Jackalope
AMD Athlon XP 2500+ 1837 MHz
1GB RAM
ATI Radeon 9600 (as I'm pretty stupid at this, I can't get the latest drivers - ATI Catalyst 9.3 - to install. [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English))
WINE 1.1.26

**Other:** I've pretty much completely disabled everything in Compiz except for the Window Decoration so I can see the window buttons.

I've also tried editing the xorg.conf file, although I'm not sure it looks right?
```
Section "Device"
          Identifier          "Configured Video Device"
          Option              "Capabilities" "0x00000800"
          Option              "UseFastTLS" "off"
          Option              "KernelModuleParm" "locked-userpages=0"
EndSection
```I've also added these lines to the WTF file and made sure the permissions are set to read-write:
```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET UIFaster "2"
```My computer runs WoW fine with XP, but I know things are gonna be different with Ubuntu.

I probably shouldn't even be using a Linux OS, as I'm not the smartest with computers, and extremely Linux-stoopid.  I apologize T_T.  Any help would be awesome~

P.S. If it matters, I'm attempting to run Wrath of the Lich King with the latest patch.

---

### Post by Celexi on 2009-08-06
mind posting your config.WTF file? obviously edit out your account name.

Edit: nevermind, didn't see it. Can you check in the in-game graphical options if you have projected textures or specular lighting activated?

---

### Post by Killer Mangos on 2009-08-06
> **Celexi said:**
> mind posting your config.WTF file? obviously edit out your account name.

Edit: nevermind, didn't see it. Can you check in the in-game graphical options if you have projected textures or specular lighting activated?

I tried changing the spectral and projected textures value to "0" in my WTF.

This time, my monitor went black with some barely there fuzzy lines, and test that said:
"Not Optimum Mode
Recommended Mode:
1280 x 1024 60Hz
(yellow box with question mark)"

But then I rebooted my computer, and brought up the config.WTF and the two lines I edited were missing!  So I deleted the file and booted up the game to make a new one, and the game now works!  I was able to change the resolution, and turn all the effects either 'off' or on the lowest quality possible.  My character face on my health bars don't show up, but I don't care since the game is running now. 

Thanks so much!!!
[B]
Problem solved![/B]

---

### Post by gjoellee on 2009-08-06
I am saying it to you as I do with everyone else:

WINE 1.0.1 is the latest stable version
WINE 1.2.26 is the latest develpment version, which means that it is not stable and you should use it with great care!

Using the stable verison of WINE might solve your problem.

---

### Post by Killer Mangos on 2009-08-06
> **gjoellee said:**
> I am saying it to you as I do with everyone else:

WINE 1.0.1 is the latest stable version
WINE 1.2.26 is the latest develpment version, which means that it is not stable and you should use it with great care!

Using the stable verison of WINE might solve your problem.

Ehehehe, I couldn't figure out which one was the stable version, as 1.1.26 is the one that's posted on the main page and I couldn't get to any other dl links.... BUT!  The problem is solved, so I'm not about to go messing with it now.  Thanks though =)

---

