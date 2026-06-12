---
title: "Nub: EvE // Cs:S // ATi // Wine"
date: 2009-08-11
forum: Wine
---

### Post by xerobasix on 2009-08-11
I'm having issues with my wine setup launching eve online. I have the latest version; used some launchpad repo's i found. I'm also using the catalyst 9.7 driver and have tried the suggestions @ winehq to no avail. I wouldn't post about this but I couldn't track down any forum similar threads...

Problem: Eve won't launch but instead crashes with an error message that says something to the effect of "Exe.exe has encountered..." System monitor shows eve as being in "zombie" status. I tried to add a reg edit in Software/Wine/Direct3D, but there was no direct3d entry. I'm wondering if I forgot to install some dependency or if I overlooked something... Counter-Strike runs but extremely slow in firefights.

TLDR: no direct3d key in /software/wine/______ <---

any help would be appreciated, thx.

Hardware: Asus ATi 4830 Superclocked

//Edit1//
Error Message is: "The program ExeFile.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience."
//Edit2//
Fixed with $ sh winetricks d3dx9; Figured out troubleshooting is easier if the .exe is launched from terminal.

---

