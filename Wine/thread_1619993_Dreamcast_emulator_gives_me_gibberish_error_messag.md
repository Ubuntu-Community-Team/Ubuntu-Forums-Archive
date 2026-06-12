---
title: "Dreamcast emulator gives me gibberish error message!"
date: 2010-11-12
forum: Wine
---

### Post by abcd_z on 2010-11-12
Lubuntu 10.10
Wine 1.2.1

I'm trying to run the Dreamcast emulator NullDC.  The GUI loads with the menu, but before I can access anything an error message pops up.

It's in gibberish.  The menu bar is in english, but the message itself is a combination of squares and japanese/chinese symbols.

The error message was probably telling me that I didn't have the dreamcast bios, because once I put the flash and BIOS files in their right places, I got a different gibberish message.  It took me to a plugins screen, and here's the other problem: it doesn't recognize any of the plugins.

The plugins are for sound and graphics rendering and stuff like that.  The .dlls are located in the same folder as the .exe file (the linux folder, not the pseudo-c drive), but for some reason NullDC doesn't seem to recognize them.  I tried copying them to c:\windows\system since that was where a previous .dll file went, but it didn't change anything.

The drop-down menus for the plugins are completely blank.  If I hit "cancel", it'll give me yet another gibberish message, and if I hit "okay" the damn thing crashes on me.

I tried with both NullDC 1.03 and 1.04, r50.  Both of them have the exact same problem.

I just wanted to play Sonic Adventure... TT_TT

EDIT: Used Winetricks to install all the DLLs, works fine now.

---

