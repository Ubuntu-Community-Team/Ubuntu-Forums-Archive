---
title: "Games wont run in wine?"
date: 2011-02-04
forum: Wine
---

### Post by EpicMe on 2011-02-04
I am a big linux noob, and I am trying to learn it as well as I can, so if I am posting something thats already been posted, or that is a simple fix, just help me out. (: thanks!

Anyways, I install games perfectly with play on linux from my DVD copy of the games, and everything goes fine until I try to run it, and it's like I never clicked on it. 

I know that this can work because there are videos on youtube of people playing almost any game they want with wine. 

I am running Zorin OS 4 core 64-bit, which runs off of Ubuntu 10.10

Any help is much appreciated!

---

### Post by cogadh on 2011-02-04
It might help if you told us what games you are trying to run. Without knowing what games you are running, I would guess that chances are the problem is the copy protection on the games. Wine does not support all copy protection schemes, so in order to run them in Wine, you might need to use a "cracked" executable. Don't ask where or how to get a crack, they are a forbidden topic on these forums due to their legally questionable status.

---

### Post by EpicMe on 2011-02-05
Some games I have tried running are,  borderlands, call of duty black ops, mafia II, need for speed undercover, runes of magic, perfect world, and that is about the jist of it. 

None of them seem to do anything, mafia II has a cracked executable, runes of magic, and perfect world are completely free games.

Thanks for your time so far, it really is much appreciated.

---

### Post by dino99 on 2011-02-05
[http://appdb.winehq.org/objectManager.php?sClass=category&iId=2&sAction=view&sTitle=Browse+Applications](http://appdb.winehq.org/objectManager.php?sClass=category&iId=2&sAction=view&sTitle=Browse+Applications)

winetricks, playonlinux, wisotools can help too

---

### Post by EpicMe on 2011-02-05
Thanks for your time, but that did not help.

All drivers are installed, and all updates are in.

I can run basic programs with wine, but when it comes to games, it just doesn't run... I'm not sure if I did anything wrong.

---

### Post by Suroh66 on 2011-02-05
You checked all the common minor things to right? like right clicking the launcher going to the permissions tab and checking the box next to "is executable". Did you install these games properly do you try playing around with the graphics settings. Like suggested before get winetricks and figure out if your missing any thing at all if you're chances are you can get it quick. And just for fun google the problem you're having with these games (one at a time of course) and you may find your fix their. And if it was a problem with copy right protection that would probably only effect black ops if even that and also most of the time you encounter that problem the launcher will go but the game will not. I've seen many games do this and I've seen some not :(

---

### Post by EpicMe on 2011-02-06
I have been all around Google searching for an answer, but I seem to be having a unique problem. I installed winetricks, and fooled around with installing missing items, and no such effect happened. The games are installed properly, Most of them have been installed with play-on-linux.

---

### Post by nasul on 2011-02-07
Simple games will work but use Cedega for more complex ones.

---

### Post by EpicMe on 2011-02-07
I really dont have the cash for Cedega, and even if I did buy it, I have a feeling it might not work. Does anyone know how I can get these games running? Like what am I missing?

---

### Post by matt_symes on 2011-02-07
Hi

Run the wine application from the terminal. What errors do you get ?

Kind regards

---

### Post by EpicMe on 2011-02-07
Thanks for your time so far, but could you give me an example code to type into the terminal?

---

### Post by matt_symes on 2011-02-08
Hi

It will be something along the lines of (in the terminal).....

```
wine "c:\\Program Files\\Game Folder\\Game name.exe"
```

depending on where it installed under your hidden .wine folder in your home directory.

Kind regards

---

