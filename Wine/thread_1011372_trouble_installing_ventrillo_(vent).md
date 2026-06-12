---
title: "trouble installing ventrillo (vent)"
date: 2008-12-14
forum: Wine
---

### Post by Dontechjuan on 2008-12-14
I'm trying to get ventrillo to work so i can use it while playing WOW and other online games and i am having a little issue. I started out by following these directions i found
--------------------------------------------------------------------------------------------
First : Make sure you have the newest version of Wine setup and installed.

Second : Download Ventrilo for Windows (Here) and install it under Wine.

Third : Now Vent at default requires the use of an audio codec called GSM 6.10, and from my own experience this codec/driver is not included in WINE right of the bat, so youll have to get the file msgsm32.acm (here) and place this file in your system directory under Windows in WINE (you may also try putting it in system32 which is fine, i actually put in both spots to be sure).

Forth : goto the Windows directory (should be /home/.wine/drive_c/windows) and open the file named system.ini and place this line in it under the drivers32 section (for organization sake)

    MSACM.msgsm610=msgsm32.acm

ok now you may not have to, but I restarted my computer

Voila! You should now have Vent working, now you may get some errors, but they shouldnt hinder your use to voice chat, as well I have found out and it may only be on my computer and not others but Overlays wouldnt work, but i think it was hardware issue, youll just have to try it out yourself! I hope this helps any of you having trouble with getting this working, also make sure to keep an eye out, the guys who develop Vent are working on a Linux client! Enjoy.
-----------------------------------------------------------------------------------------
ok i did everything step by step. however step 2 "install under wine" is where im having problems. I tried puting it in the .wine/drive_c folder and double clicking nothing happens, right clicking and click open under wine nothing happens and i tried opening the terminal and trying to open in the same manner that you install most games "wine /pathtofolder/vent.exe" and it just says cannot find folder. so how the heck am i supposed to install it?! am i not typing in the correct path on the terminal? i dont have any problems installing games off the cd. the exact line i type into the terminal is "wine /drive_c/vent.exe" because thats where i put the folder and i changed the name of the vent.exe to vent.exe because it was a name with spaces and symbols that confuse the terminal so i dont know what else to try. it seems to me that this would of and should of been an easy task, but whatever. please help me

---

### Post by Dontechjuan on 2008-12-14
nevermind im a damn r-tard lol. i figured it out. But just in case anyone else is having this problem though ill tell u what i had to do to fix it. remember how i said i typed in the path "wine /Drive_c/vent.exe" under the terminal? well i was only part right. you have to go back further on the pathway.Assuming that i named my computer "donscomp" when i installed ubuntu in the first place i had to type this path on the terminal "wine /home/donscomp/.wine/drive_c/vent.exe" and it finally worked and now i feel like a big R-tard, but hey live and learn right? lol

---

