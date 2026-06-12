---
title: "City of Heroes help"
date: 2009-03-23
forum: Wine
---

### Post by lufo4 on 2009-03-23
hello, i decided to switch to ubuntu and now i want to play city of heroes, so ive kept my windows partition. i've tried wine, and after getting help with part of wine, it wont load past the launcher, then i tried WineCVS, which is where i get many errors, is there any painless way, or a comprehensive tutorial to install it, i've heard about cedega, but i dont want to pay the extra subscription fee for just one game,

---

### Post by ajackson on 2009-03-23
The [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980") page is a good place to start and/or ask questions. CoH does work pretty well with Wine as I used to play it a few months ago with no problems.

---

### Post by lufo4 on 2009-03-23
well, ive tried many different versions of wine, but they all crash while the updater is running

---

### Post by darck1 on 2009-04-19
I've had much the same lack of success. Even tried compiling Wine from the source code with no luck. I'm on an AMD-64 machine running Jaunty. I've tried Wine, ULL - nothing. Wine freezes on the "Accept" screen of the launcher and I couldn't even get that far with ULL.

---

### Post by NightMKoder on 2009-04-19
The appdb page say to run it like
```

wine CityOfHeroes.exe -project coh

```

to skip the license(?). Have you tried that?

---

### Post by lufo4 on 2009-05-03
what i have done is a fresh install of jaunty, without removing the old packages, installed wine 1.1.19 and it runs fine ( i just double click on next, to skip the eula) now i can switch to ubuntu full time, however, i have another problem. when i play the game there is no sound whatsoever, the speakers are up, the computer volume is up, the game volume is up but no dice. so when i close it out properly (quit>quit to destop>exit now) the sound plays nonstop, it sounds like the music for eitehr the downloader or the first screen any help?

---

### Post by ashavohu on 2009-05-03
I don't know if you've done this yet or not, but ...

To get sound from City of Heroes in WINE you must go to Configure WINE (under Applications: WINE), click the Audio tab, and select OSS driver as the sole output. You should get perfect sound after that.

By the way, are you using AMD/ATI 790GX integrated graphics? I'm hoping to hear from someone that they have success using Jaunty + ATI before I make the jump. I'm using the original version of Intrepid + WINE 1.0.1 with no updates due to difficulties with graphics compatibility.

---

### Post by legine on 2009-05-03
Just tried CoH.
I can install useing the lates wineversion from winehq (On ubuntu I think you can  pull that in via upget if you enter the right channel)

The Game installes fine. When you get to the Licens screen you need to press the agreebutton fast (before it crashes.)

You can try to do a slow doubleclick :)

Cheers Legine.

lufo4: What crashes, where?

---

### Post by lufo4 on 2009-05-03
well so far the game doesnt crash, in fact, graphically and gameplay wise it runs better, but the soudn doesnt work, and i dont know how to configure wine because i have installed an older verison and i dont have the entry in my applications menu

---

### Post by lufo4 on 2009-05-03
also, how can i configure the sound with wine through the terminal?

---

### Post by lufo4 on 2009-05-03
ok, about the gui thing i just installed the same version from wineHQ, my bad. however when i select the oss drivers, i dont hear any sound and the sound test fails

---

### Post by lufo4 on 2009-05-04
After playing around with it all i did was install a new version of wine and everything works now

---

