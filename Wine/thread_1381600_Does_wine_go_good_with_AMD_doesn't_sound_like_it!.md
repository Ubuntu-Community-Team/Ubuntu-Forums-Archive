---
title: "Does wine go good with AMD? doesn't sound like it!"
date: 2010-01-15
forum: Wine
---

### Post by antiwindowsman on 2010-01-15
Hi I am using wine for the first time and have it on hardy .04 I am using a amd Athlon on a asus motherboard, this board has more chips on it than a can of pringles.  I installed StarCraft the non NT ver.  (oldist). it plays and it has sound at startup but after the splash screen , no sound . I have tryed and am still trying differant things in the wine config tool but haven't had any luck, Can anyone help with this?  I also have the same game only it is the NT ver. on a newer pen4 using ubuntu 64 bit desktop 9.10 it works fine and so does everything else.  In fact it installed right of the bat and has never gave my brother ,a complete non computer user, any trouble whatsoever.

---

### Post by lukeiamyourfather on 2010-01-15
Sounds like you need to use the newer installer for StarCraft. The processor has nothing to do with Wine compatibility, could run it on a 486 for all it cares.

---

### Post by Dark_Stang on 2010-01-15
What version of WINE are you using on the 8.04? Probably not the latest. Also, I'm running AMD processors in all my machines and had no issues playing WoW and running Photoshop CS2 through WINE.

---

### Post by antiwindowsman on 2010-01-15
Thanks ill try that next, I too have some experience with python, by the way., I once made it say "Hello World", and that is about the extent of my programing. So thanks.

---

### Post by antiwindowsman on 2010-01-15
wine was installed using the synaptic installer yesterday , it should be up to date, I think.

---

### Post by antiwindowsman on 2010-01-15
I have tryed both the 1,0 ver of starcraft and the win95,nt ver both are the same. Sound in the splash screen then no sound at all.

---

### Post by antiwindowsman on 2010-01-15
OK I got it running!! what I did was to go to the download site for wine and downloaded and installed the beta ver. of wine 1.1.36 for amd64, witch is what I thought I had, WRONG,, and it told me so. So I uninstalled it and tried all 3.  the wine 1.1.36 I386 was the only one to install without a Red string of text telling me Wrong architecture.  Then after more trial and error I found the Wine config audio had to be set to EsounD with no other selected.  Also I followed the instructions given here on this forum telling me to right click and select open with other..... and then selecting Wine Windows launcher .  Thanks Sticky.  StarCraft plays well and I installed and tried Both the 1.0 ver. and the Win/NT ver. Both work.

---

