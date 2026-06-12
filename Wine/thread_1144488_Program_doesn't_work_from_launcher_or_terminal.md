---
title: "Program doesn't work from launcher or terminal"
date: 2009-04-30
forum: Wine
---

### Post by mfox on 2009-04-30
I recently installed Globallink, an old commercial translator package, on Ubuntu 9.04 on wine.  The installer didn't make it all the way through, but the program did install nevertheless.  If I navigate to the program in drive_c and click on the .exe file, it runs fine.  But if I try starting it from a terminal or make a launcher for it and put it on a gnome panel, it doesn't work.  Starting it from either of these modes gives, first a segment fault and then a message that the translator engine couldn't load. It then quits. 

I have never encountered this type of problem before where it starts fine one way (clicking on the file) but not the other ways (terminal or launcher).  Any idea what's going on here?  Is there an easy way to fix this?

---

### Post by Meow27 on 2009-04-30
from what it sounds like, wine is designated to load, exe files from the gnome user interface only.... i dont think this will work, but try cfompletely removing whine from the synaptic package manager and reinstall it..

again no garantuess, i dont think it will work but its worth a try

---

### Post by cogadh on 2009-04-30
When you launch from the terminal, try changing directories to the application's install directory first, then run it.

---

### Post by mfox on 2009-04-30
Thanks for the suggestions, but neither one works.  This is quite a mystery.  I can build launchers for all other wine programs but this one.

---

### Post by khormin on 2010-08-09
Also experiencing this problem, though it's for a few windows programs, albeit none the one listed by the OP.

Attempted listing this problem on AppDB, but didn't have any response.

Opening the programs (using "Black & White 2" for example) from a launcher automatically fails. Attempting to load the programs from the terminal fails, bringing the following error.[INDENT]~$ wine "/home/USER/.wine/drive_c/Program Files/BW2/white.exe" -opengl
fixme:heap:HeapSetInformation 0x2e5a000 0 0x269fd34 4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x269f764,0x269f768): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x269f764,0x269f768): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x269ef38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x269f0b8,0x00000000), stub!
[/INDENT]Attempting to load the program in terminal after cding to the directory (BW2 from the above example) brings a list of d3d errors, but otherwise loads the program.

Attempting to load the program via nautilus and activating the exe manually allows the program to load.

Is there a fix for this? I have attempted adjusting the default loader for .exe files to wine, have attempted a #! bash fix, to no avail.

---

### Post by khormin on 2010-08-09
Forgot to mention - issue has existed from wine 1.3.0, 1.2, and 1.1.43

---

