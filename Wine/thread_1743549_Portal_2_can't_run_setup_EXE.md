---
title: "Portal 2 can't run setup EXE"
date: 2011-04-29
forum: Wine
---

### Post by razor7 on 2011-04-29
Hi, i have ubuntu 10.04 and Wine 1.3.17, but when i try to run Setup.exe i get an access violation.

Steps i followed:

Created folder /home/user/wine/Portal2

On terminal ran:
export WINEPREFIX=/home/user/wine/Portal2
winecfg
after that ran cd /media/Downloads/games/Portal2
and finally wine Setup.exe

I get this error "Access violation at address 00409B2A. Write of address 00400000."

Should I install something before with winetricks?

Please advise.

Thanks a lot!

---

### Post by wandering_cat on 2011-05-03
Maybe you downloaded setup files to the Windows HDD part? I mean, on my laptop I have Ubuntu 10.10 installed with Windows, & I just moved setup.exe & other files for Portal 2 from my 
*media/windows/downloads/games/portal 2*
 to the other directory which is in the Linux's HDD part (for example, */home/downloads/portal*).

setup ran successfully)

*sorry for my English, I could've made mistakes as it's not my native language.

Good luck!

---

