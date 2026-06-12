---
title: "Problems installing Civ 3"
date: 2009-07-08
forum: Wine
---

### Post by taylorsmithereens on 2009-07-08
I found the following at appdb and ran into a few problems. 

> * Download wine-0.9.46 source. 
 * Apply the patch from: [ bugs.winehq.org/show_bug.cgi?id=3498 ]("http://bugs.winehq.org/show_bug.cgi?id=3498") 
   (I suggest that you remove the line FIXME(":stub\n"); at line 1806 in dlls/gdi32/freetype.c as well. Less prints.) 
 * Compile wine and install. 
 * Copy all 3 Civlization Complete CDs to your harddrive. 
 * Copy dsetup.dll from the directx/ directory to the same directory as setup.exe is located. 
 * Run winecfg and tell wine to load native windows dsetup.dll for setup.exe 
 * Run  setup.exe  
 * It will still complain about missing dsetup.dll, but installation continues anyway. 
 * Install the game. 
 * Meanwhile, find a no-CD patch for Civilization Complete (Conquest v1.22) 
 * When asked for the "CD 1" give the path where you install from. The installation will just plainly quit afterward, but it is complete. 
 * Install the no-CD patch. 
 * Run regedit and set DirectDraw renderer to GDI: 
   HKEY_CURRENT_USER\Software\Wine\Direct3D\DirectDrawRenderer="gdi" 
   (Remember, this is a global setting, you might have to reset it to opengl for other games.) 
 * Run Civ3Conquest.exe with the custom build wine. 
 

I'm rather new to Ubuntu and am still at a fairly basic level, so a bit more explanation than usual might be in order.

How do I "Run winecfg and tell wine to load native windows dsetup.dll for setup.exe?"

After nearing the end of installing the first disk I got the following error message:

> Feature transfer error

error: -1603 fatal error during installation


Any ideas would be more than appreciated, thanks in advance.

---

### Post by jacksaff on 2009-07-08
Those instructions are pretty old.
Unfortunately the news is pretty bad. 
Civ3 is currently rated 'garbage' on wine's appdb which means you basically have zero chance of getting it running. 
There aren't many comments there which suggests not many people are trying to get it going so I wouldn't hold out much hope of this changing any time soon...
Sorry.
Civ4 on the other hand, runs just fine.

---

### Post by taylorsmithereens on 2009-07-09
Well, I held out for awhile but it's time to get 4.  Thanks for the info.

---

