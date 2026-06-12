---
title: "Mouse Invisible on update to Wine 1.1.42"
date: 2010-04-08
forum: Wine
---

### Post by Daddyo-613 on 2010-04-08
**The Problem:** I just updated to WINE 1.1.42 when I run Red Alert 2 Yuri's Revenge the mouse is not visible on the menu screen. The mouse functions if I'm lucky enough to hover over one of the buttons but I can't see the mouse cursor. The mouse and cursor seem to work normally during actual game play. It was working before I upgraded to the newer version of WINE.

I know I can try going back to an older version but what I'd like to know is whether there are any settings I should try first. I'd also like to know if anyone else is experiencing similar problems with this latest version of WINE.

**My Settings:**
OS: Ubuntu: Karmic 9.10
Gnome: 2.28.1
Kernel: 2.6.31-20-generic-pae
CPU: Intel Core2 Quad @2.4GHz
Video Card: nVidia GeForece 8600,GT
Driver: nVidia 195.36.15

**My Wine Settings for RA2MD.exe:**
Version: 1.1.42
Additional Libraries: none
Sound: OSS, Hardware Acceleration=Full, 
Default Sample Rate=48000, Default Bits Per Sample=16
Graphics: Window Settings: Allow window manager to decorate windows and control
windows enabled, other options not enabled
Direct 3D: Vertex Shader Support=Hardware, Allow Pixel Shader=enabled
Screen Resolution=96 dpi
Registry Edits: DirectDrawRenderer=opengl and RenderTargetLockMode=readtex

---

### Post by sionco on 2010-04-10
I have the same problem but with a different game, Football Manager 2010, the mouse has disappeared.

---

### Post by Daddyo-613 on 2010-04-10
Sionco;

Thanks for responding. Can you tell me if your mouse cursor went missing after you updated to WINE 1.1.42? 

If there are more people out there who are having the same problem then the problem is probably in WINE and there might be a Registry Edit that could fix it.

In your case, does the cursor disappear only on the menu screen or is it not visible during game play as well?

---

### Post by sionco on 2010-04-10
> **Daddyo-613 said:**
> Sionco;

Thanks for responding. Can you tell me if your mouse cursor went missing after you updated to WINE 1.1.42? 

If there are more people out there who are having the same problem then the problem is probably in WINE and there might be a Registry Edit that could fix it.

In your case, does the cursor disappear only on the menu screen or is it not visible during game play as well?

Yes, it definitely was working before I noticed the upgrade to 1.1.42.

And Yes, the cursor is missing, through the whole game.  The game definitely detects where it is though, as the buttons as I move the invisible cursor over them.

---

### Post by sionco on 2010-04-10
I've just tried installing a second time using playonlinux, which I believe uses a previous version of wine(i'm not totaly sure) and the cursor appears fine there. 

Yet the original normal install I had (without playonlinux) the cursor is missing after the update.

---

### Post by Daddyo-613 on 2010-04-11
Thanks for the clue. I've been investigating further. It seems that some changes as to how the cursor is handled were made in WINE 1.1.42.

I checked the WineHQ site and found this link to a description of the changes incorporated into ver. 1.1.42: [http://www.winehq.org/announce/1.1.42](http://www.winehq.org/announce/1.1.42)

Note the two lines in the description:
 
```
server: Add support for storing the cursor and show count in the thread input structure.
user32: Store the current cursor and show count in the server.
```

There are also some bug reports coming in about losing "Hardware Cursor" functionality but nothing conclusive yet.
If others come across similar problems or bug reports let us know. 

The problem with the cursor disappearing only on certain screens sounds like something that can be fixed. 
We just have to figure out what registry entries are needed.

---

### Post by twigusa on 2010-04-14
Hi,

I'm getting the same issue after upgrading to wine 1.1.42 running Chessmaster 10. I'm running Lucid and had some problems with compiz - they are now resolved but the issue with the mouse pointer in wine still remains.

Cheers,
Twig.

---

### Post by Daddyo-613 on 2010-04-23
Wine 1.1.43 is now out in binary. I had complied it from source before the binary version was released but it only made things worse. The problem was likely the way I complied the program and not the program itself. 

In any event, 1.1.43 installed easily from the repository. Unfortunately it doesn't affect the invisible cursor on the game menus.

There must be someone out there who has an idea how to get the cursor working or why it disappears in the first place.

Any help would be appreciated.

---

### Post by Dav13s on 2010-04-30
I have the same problem with FM2008, although it was working fine until I went from 9.10 to 10.04. I'm running Wine 1.1.42, but I think it may have upgraded when 10.04 was installed. Any help would be appreciated

---

### Post by .bandi on 2010-05-02
Hi

First: sorry, my English is not good.
I have same problem, but i have an idea what help out:
1. Remove wine from your computer
2. Download an older wine package with wine1.2, wine-gecko, etc...
3. Install this packages
4. Lock versions for this packages in Synaptic package-manager
5. Install winetricks, FM.

It's works for me, this steps helped me for visible mouse, and i can play FM2010 now.

I have downloaded 1.1.39 .deb files from here: [https://launchpad.net/ubuntu/+source/wine1.2/1.1.39-0ubuntu1/+build/1520772](https://launchpad.net/ubuntu/+source/wine1.2/1.1.39-0ubuntu1/+build/1520772)

Good Luck!

---

### Post by Daddyo-613 on 2010-05-11
I just installed Wine 1.1.44 and the disappearing mouse cursor problem is gone. At least for Red Alert 2 Yuri's revenge.

Others who reported similar issues with Chessmaster 10 and FM2008 should install 1.1.44 and let us know if the update solved your problems as well.

TTFN

---

### Post by eighty4 on 2010-07-30
Just in case anyone else is having the same problem, I've installed Wine 1.1.44 as Daddyo-613 suggested and the cursor is visible again.

The problem came after upgrading Ubuntu, at which point I guess Wine was updated to 1.1.42.

---

