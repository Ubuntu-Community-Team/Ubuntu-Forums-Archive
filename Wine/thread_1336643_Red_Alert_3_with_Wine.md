---
title: "Red Alert 3 with Wine"
date: 2009-11-24
forum: Wine
---

### Post by xnerdx on 2009-11-24
Hey everyone, I bought C&C: Red Alert 3 quite a while back but never had good enough hardware to actually play the game. Back in July I built my own computer with some very advanced hardware, well above that of the recommended hardware requirements for C&C: RA3 but I looked up support on Wine and it seems to be barley alive. Accordingly there is a case where someone got the game to run, but I have no such luck. I installed it with ease, everything but the Gamespy addon because it requires .net frameworks and the EA Download Manager. The game is installed but when I try to run it the logo screen comes up and disappears after a minute or two. Using the terminal I get this error:
```

wine: Unhandled page fault on write access to 0x001f0000 at address 0xb7cb5896 (thread 002e), starting debugger...

```
I am running 9.04 and I ran update manager before I installed the game, I tried to install/run it with both win and POL (Play on linux). If anyone knows a way to fix this I would be very grateful! Thank you

--Michael

---

### Post by xnerdx on 2009-11-24
*  Download Wine 1.1.2, the cursor patches and the volume name patch
    * Unpack the Wine archive through the file manager or with 'tar -xvjf wine-1.1.2.tar.bz2'
    * Enter the Wine directory with 'cd wine-1.1.2'
    * Apply the cursor patch with 'patch -p1 < ../cursor-patches-1.1.2.patch'
    * Apply the volume name patch with 'patch -p1 < ../volume-names.diff'
    * Update wineserver with 'tools/make_requests'
    * Configure Wine with './configure --prefix=$HOME/wine-ra3', where you can choose another install path if you want to. If it displays
      any errors and you are unable to fix them yourself, post the error message here, without the full console output
    * Build Wine with 'make'
    * Install with 'make install'
    * Delete the Wine source with 'cd ..; rm -rf wine-1.1.2'
    * Now you can run the game by substituting the 'wine' command with '$HOME/wine-ra3/bin/wine'

Works great, sorry for the wasted post.

---

