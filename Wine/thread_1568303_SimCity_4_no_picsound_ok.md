---
title: "SimCity 4 no pic/sound ok"
date: 2010-09-05
forum: Wine
---

### Post by peterson2k4 on 2010-09-05
I was able to install SimCity 4 ok but when I go to play it, the screen goes either yellow or digitizes.  I can hear the sound of the game fine.  I already tried reinstalling the game but the same thing happens.  I have had played it on the same PC (however I was running 9.10 at the time and not 10.04) Any tips?

see images for what screen looks like

---

### Post by Strategist01 on 2010-09-05
Hi there.

I took a look on one of the SC4 forums, [www.sc4devotion.com]("http://www.sc4devotion.com"), and I found this post:

> Nice to hear that you have success in Linux too.  Here are *some* experiences I've had:

- I am running it in wine-windowed desktop mode.  You need to put **env XMODIFIERS=''** before wine ".../SimCity 4.exe" -args, if the keyboard doesn't work.

-  Game windowed mode w/ the -w argument doesn't work with software or  opengl mode.  gdi can work, it's slower, choppy, and you may need to set  the custom resolution to run at the same mode as you have X (e.g. X  running at 1650x1050 at 24-bit = -r1650x1024x24 ... not 16 or 32) to  increase performance, since the graphics won't have to be recalculated  into a different depth.  Stick with opengl.

- Registry tweaks are  for modifying performance, they aren't prereqs for the game.  The only  two you need to explicitly put are VideoMemorySize and  DirectDrawRenderer.

- Graphical issues, especially 'residue' from  the query tools, are common, and shadows are always stuck to low  quality, regardless of setting.  

- No 'native' Windows .dlls are  needed to run SimCity 4 Deluxe (though some are needed for the 3rd  party programs); the ones with Wine are sufficient.  

- You could  copy DirectX files into Wine's system32 folder, and then change the  registry and shortcut settings to reflect.  Overall graphics performance  is subjectively better (speed, shadows, no artifacts), but automata are  messed up.

I have 1.8GB of plugins and DatPacking has greatly  improved performance (50 sec first loading time, 20 sec successive  loading time).  I use Windows in VirtualBox to run the 3rd party  programs w/o having to boot back into Vista.  Also, I had the blank text  bug/crashing problem.  I thought it was due to file names (which I  still haven't ruled out), but DatPacking has solved this problem too.

I  have got to try cdemu.  I need the nightlighting patch for some  potential mayor diary pictures.  Though, does it have the same behavior  as like Daemon Tools: having to unmount, then remount the file if you  close the game the first time and go back in the game?

That might help. Other wise, go to the forums, search for "SC4 wine" (w/o quotes) and you should find some more info.

Hope that helps :)

---

