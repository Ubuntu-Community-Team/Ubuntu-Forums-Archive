---
title: "WoW with wine"
date: 2008-12-26
forum: Wine
---

### Post by natpagle on 2008-12-26
Hello! I have followed step by step instructions on the installation of WoW within wine.  I am having a few issues that I can't seem to correct with my VERY limited knowledge of Linux troubleshooting.

My relevant specs are as follows:
Ubuntu 8.10
Wine 1.1.10
World of Warcraft WotLK, Fully patched
ATI Radeon X1950 Pro
**************
         fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.8304 Release
**************
2GB RAM 

I have tried all of the tweaks and troubleshooting techniques contained within the forums.  I am running in windowed mode at the moment.  I have added the 4 DLL's.  When I run in OpenGL mode, my screen throws polygon's everywhere.  D3D mode runs the same as Direct3D.  Occasionally the game stays on the login screen enough to where I can see the dragon's full animation.  On this occasion, my screen is stuttering, as well as the audio.



I continue to receive error 132(this happens as soon as I get to the login screen) (I would post it but the forums keep saying I have 15 images in the post)

Can someone help?

---

### Post by wimpie on 2008-12-26
You got the same problem like: [http://ubuntuforums.org/showthread.php?t=1022049](http://ubuntuforums.org/showthread.php?t=1022049)

I think at least maybe you can find a solution there soon..

Greetings Wimpie

---

### Post by natpagle on 2008-12-27
I have gone through just about everything recommended in those posts, to no avail. OpenGL mode no longer shows distorted graphics, but is still as choppy as D3D and the cursor (due to the lack of OpenGL support for hardware cursor) moves at the same rate as my game. 

I tried both registry tweaks.  The first one I had done beforehand, the second - I couldn't find the Direct3D folder in:

> HKEY_CURRENT_USER\Software\Wine\Direct3D\

---

### Post by DoktorSeven on 2008-12-27
> **natpagle said:**
> 
I tried both registry tweaks.  The first one I had done beforehand, the second - I couldn't find the Direct3D folder in:

You have to create that (rightclick Wine, New, Key, name it Direct3D (case sensitive).

---

### Post by emshains on 2008-12-27
> **natpagle said:**
> Hello! I have followed step by step instructions on the installation of WoW within wine.  I am having a few issues that I can't seem to correct with my VERY limited knowledge of Linux troubleshooting.

My relevant specs are as follows:
Ubuntu 8.10
Wine 1.1.10
World of Warcraft WotLK, Fully patched
ATI Radeon X1950 Pro
**************
         fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.8304 Release
**************
2GB RAM 

I have tried all of the tweaks and troubleshooting techniques contained within the forums.  I am running in windowed mode at the moment.  I have added the 4 DLL's.  When I run in OpenGL mode, my screen throws polygon's everywhere.  D3D mode runs the same as Direct3D.  Occasionally the game stays on the login screen enough to where I can see the dragon's full animation.  On this occasion, my screen is stuttering, as well as the audio.



I continue to receive error 132(this happens as soon as I get to the login screen) (I would post it but the forums keep saying I have 15 images in the post)

Can someone help?

Have you tried disabling glow and death effects ?

---

### Post by natpagle on 2008-12-28
Ok, added the 2nd, registry key.  Thanks for the tip Dok.

On a good note, I have opened the game about 30 times and let it run a few times for probably 2 hours, and I haven't received an Error 132.  Now my graphics are just choppy 100% of the time.

I have tried every combination of the video settings within WoW itself.  At the moment I have everything down to it's lowest settings. Nothing but the following options are checked and I have tried with and without them.

[X] Hardware Cursor
[X] Reduce Input Lag
[X] Windowed Mode

---

### Post by natpagle on 2008-12-28
Back to error 132 upon loading of game. Choppy graphics at logon screen, 132 when i'm loading game. I'm depressed. :(

---

