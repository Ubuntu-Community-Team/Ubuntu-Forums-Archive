---
title: "Problems running Oblivion in Wine."
date: 2010-05-23
forum: Wine
---

### Post by Dormorn on 2010-05-23
Hello i recently decided to try and play The Elder Scrolls IV: Oblivion so i installed the game and its expansion's and had no problems. When i try to run the game now it opens fine and i go thorough the opening titles and into the main menu. Here the title isnt shown for a few seconds and i cannot see the mouse pointer. after a while the screen starts to flicker and i can see the title and mouse during these rapid flickers. When i begin the game the first cut scene plays perfectly but when the game play starts my character is nearly see though and is missing an eye. The menu to configure my character is transparent. i haven't gone any further than this, any help is greatly appreciated. I am running Ubuntu 10.04 and i am very new to it.

---

### Post by Progressive on 2010-05-24
When you post questions you need to specify which hardware you are using and which version of wine you are running. Have you applied all the official patches to the game?

Are you using the latest graphics drivers? You need proprietary drivers to play, and often it will only work with Nvidia. 

Though, the bleeding edge open source ATI drivers are starting to work for certain games.

Be sure to check out [this guide]("http://www.uesp.net/wiki/Oblivion:Linux")

---

### Post by Dormorn on 2010-05-26
sorry i haven't checked back here in a while, sorry about not posting my hardware and the drivers were the problem, thank you.

---

### Post by Trolleo on 2010-12-23
I'm having issues as well. First of all I'm new to Linux and Ubuntu. I'm running Ubuntu 10.10 and Wine 1.2.2 as far as I can tell. I've installed Oblivion, but when I open the Lauch page and click "play," it tells me something like: Unable to find CD/DVD on this computer, and doesn't take me any further than that.

Any help that can be offered to this newbie would be greatly appreciated.

---

### Post by RoflHaxBbq on 2010-12-23
Trolleo, you need to map your cd drives mount point to D:\.

Click Applications-Wine-Configure Wine

Then click on the drives tab.

You will see a few drives, for example:

C:\ drive_c
Z:\ /
H:\ ~/

Or something like that.
Click the Autodetect button.

Now there should be one that says
D:\ *Something*
Click it, click browse,
Go down to /media/, click the + sign, then click the folder that either says cdrom or Oblivion or whatever.

No click apply, ok, and launch the game.

---

### Post by Trolleo on 2010-12-23
Awesome, thanks. That worked. However, when I tried to quit it froze up on me and I'm not sure how to close.
Is there an Ubuntu analog to task manager, and if so how would I access?

Thoughts on solutions to crash?

---

### Post by Trolleo on 2010-12-23
> **Trolleo said:**
> Awesome, thanks. That worked. However, when I tried to quit it froze up on me and I'm not sure how to close.
Is there an Ubuntu analog to task manager, and if so how would I access?

Thoughts on solutions to crash?

Okay, it also crashes when I try to start a new game. I know that other people have answered this issue but as I said earlier I'm a complete newbie, so any help with this would be great.

Thanks guys.

---

### Post by mastablasta on 2010-12-24
there is a really good tutorial on how to install and run Oblivion (and Morrowind) on UESP: [www.uesp.net]("http://www.uesp.net")
 
sorry i can't post the exact wikipage for this as my access to this site is blocked here at work. :-(
it should be easy to find though.

---

### Post by Trolleo on 2010-12-24
Yeah, I've seen this one. I'm pretty sure I've done all that but still get a freeze when I try to start a new game.

---

