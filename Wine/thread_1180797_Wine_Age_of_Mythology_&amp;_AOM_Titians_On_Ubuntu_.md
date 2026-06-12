---
title: "Wine: Age of Mythology &amp; AOM Titians On Ubuntu 9.04 NO SOUND!!"
date: 2009-06-07
forum: Wine
---

### Post by Mr.Know at nothing on 2009-06-07
I Am running Ubuntu 9.04 64bit

I had a few problems in installing it and playing it but finally i got it to work.....(By using Safe Mode) (And then changing the screen fullscreen)

When  try to run AOM by clicking the shortcut icon through the desktop the splash screen stays there.. frozen and then it turns black and white...

When i try running it by the original aomx.exe  Same thing happens as the other...

But when i click on Applications > Wine > Programs > Microsoft Games > Age Of Mythology Titians (Or AOM) > Diagnostics > Safe Video

It pops out a little screen of the game so then i go to Options and change The '' Screen Size'' I Go look for 800 x 600 x 32 And click ok. And i wont ever have to do that again.. Just go to options > OK. (That might've been helpful for those who didnt know that)

So in ANY Game mode and in the menu NO SOund! 

I Have played this game on my XP And Vista So its not the CD... 

Thanks For Reading.. And Probably Answering In the future..

---

### Post by WolfRage on 2009-10-22
I know it has been awhile sine you were looking into this issue. But I too am now trying to tackle the issue of getting this game to run and run well. SO I will post agian when I have more luck.
 
What I have found to work so far:
1: Copy pidgen.dll from AOM_D1 to C:/windows/system32/
2: Download MFC42.dll (I believe that is the correct name.) and copy that to C:/windows/system32/
3: Install the game.
4: Install MSMXMLenu.msi from AOM_D2.
5: Install the version 1 to version 1.10 patch.
6: Start the game in safe video mode.
 
Alternatives: I tried installing the game using POL (Play On Linux) but this resulted in a problem with MSMXML not being detected.
So the next plan is to install the game normally but apply the patch using POL by importing the game using the POL Plugin.

---

