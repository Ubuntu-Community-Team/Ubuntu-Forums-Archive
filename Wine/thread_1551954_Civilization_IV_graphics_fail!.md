---
title: "Civilization IV graphics fail!"
date: 2010-08-13
forum: Wine
---

### Post by jedimattk on 2010-08-13
After checking the Wine AppDB this evening and seeing that Civilization IV was gold-rated, I found a tutorial for installing in Ubuntu and set about it. Pretty basic stuff: the tutorial instructed me to install the game from its DVD as usual, update to version 1.74, and add some DLLs to its program files (specifically msxml3, msxml3r, and d3dx9_36).

I ran the executable and, at first, it seemed to be playing beautifully. I didn't detect so much as a trace of lag in the opening animations. But as soon as it reached the main menu, the whole screen flickered and I found myself staring at a colorful, pixellated, utterly useless expanse. I can't give you screenshots because after that point my computer becomes unresponsive; rather, Civilization is still responsive, because I can see the colors changing and hear different sound effects as a result of button mashing. But without being able to see what I'm doing there is no way to exit Civ without hard-rebooting the computer, so no screenshots.

You'll just have to rely on my description, then, which is a lot of apparently randomly-colored lines streaking horizontally across the screen, peppered with lone pixels of other colors. It's an uninterpretable mess. I get the impression, though, that the game is still working fine behind said mess - as I mentioned before, I can apparently click on buttons and so forth; I just have no idea what I'm doing because the graphics are so messed up.

I do have proprietary graphics drivers installed for my ATI video card (its specific model is listed in my sig.) I haven't really used Wine for game emulation before, but during my last jaunt into Windows territory I became rather attached to Civilization IV, and would quite like to be able to play it in Ubuntu.

Any help you can offer would be greatly appreciated. More details are, as usual, available upon request. Thanks in advance!

---

### Post by jedimattk on 2010-08-15
Bump. Nobody knows anything about DirectX / Civ4 on Wine?

---

### Post by Zorgoth on 2010-08-15
I can't say I know why yo uare having a problem.  I have been able to play Civ IV perfectly with wine 1.3 on an ATI Mobility Radeon HD 5470.  I am not sure exactly which winetricks things I used.

To debug:

wine <path_to_civ_4> > ~/output
will save the output of your wine to a file so you can try to figure out if it is doing something wrong.  If it is a dll or a setting that is obvious the best way to fix these things is almost always winetricks (is winetricks how you are getting your dlls?  If it isn't, it should be.).

So Civ IV is responsive but you can't Ctrl-Alt-F1 out of the X session?

---

### Post by jedimattk on 2010-08-15
This is the terminal output when launching Civilization4.exe.

> fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err: ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:menubuilder: Process_Link unable to load L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Logs.lnk"
err:menubuilder:wWinMain failed to build menu item for L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Logs.lnk"
err:menubuilder: Process_Link unable to load L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Saves.lnk"
err:menubuilder:wWinMain failed to build menu item for L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Saves.lnk"
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x40068 0x00000000
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:menubuilder: Process_Link unable to load L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\CivilizationIV.ini.lnk"
err:menubuilder:wWinMain failed to build menu item for L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\CivilizationIV.ini.lnk"
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1995e0,0x19a2a8 ): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
'import site' failed; use -v for traceback
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecb0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f210,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1f4,0x00000000), stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed3c,0x00000000), stub!
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x40068
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\assets\\res\\fonts\\sylfaen.ttf", 0, (nil)): stub

I know, apparently everyone but me can run this game perfectly! And yes, I can use the Ctrl+Alt+F1 trick, but I'm not exactly adept at navigating around Ubuntu from the command line alone. I end up just typing "sudo reboot" anyway, and then what's the point? XD

---

### Post by Zorgoth on 2010-08-15
Just use "top" in the terminal

then find the bad process and type k, then the process id (which is listed in top), then enter.  If that doesn't work, quit top and type ("kill -9 <process id>")

I do not know specifically about the fixmes you are seeing; none of them obviously look like they could cause a problem like this.  I think the ATI Mobility Radeon HD 3200 is a pretty old card...  That might be the fundamental problem.  The older the ATI card, the worse its drivers are.

---

### Post by jedimattk on 2010-08-15
Well, thanks for your help anyway. :)

Any other ideas, people?

---

### Post by NeoFax on 2010-08-16
Yes, delete the d3dx_36.dll file you installed and copy over the original.  I do not know where Ubuntu keeps these as I use Arch Linux.  Now use winetricks to install Microsoft XML version 3.  You should then be able to play the game fine at this point.  There is no need to change out the Wine DirectX files for most games any more.

---

