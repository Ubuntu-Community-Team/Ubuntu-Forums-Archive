---
title: "Doom 3"
date: 2010-03-21
forum: Wine
---

### Post by bigseb on 2010-03-21
My Doom 3 came with three discs. I tried to install through Wine but it only runs the first disc then it says finished. Anyway to install (and run) this game in Ubuntu 9.10 x64?

---

### Post by Toffeeapple on 2010-03-21
Doom 3 has it's very own native linux client, no need for wine.. there is a how to do it [here]("https://help.ubuntu.com/community/Doom3") and another one [here]("http://www.blog.highub.com/linux/install-run-and-play-doom-3-on-ubuntu/") and [here]("http://www.cyberciti.biz/faq/linux-install-doom3-game/") too.. in fact a quick "[installing doom 3 ubuntu]("http://www.google.co.uk/search?hl=en&client=firefox-a&hs=l0R&rls=org.mozilla:en-US:official&ei=gHymS9KaJJuy0gSgsKzxCQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAQQBSgA&q=installing+doom+3+ubuntu&spell=1")" in google will show you some more too.

---

### Post by bigseb on 2010-03-21
> **Toffeeapple said:**
> Doom 3 has it's very own native linux client, no need for wine.. there is a how to do it [here]("https://help.ubuntu.com/community/Doom3") and another one [here]("http://www.blog.highub.com/linux/install-run-and-play-doom-3-on-ubuntu/") and [here]("http://www.cyberciti.biz/faq/linux-install-doom3-game/") too.. in fact a quick "[installing doom 3 ubuntu]("http://www.google.co.uk/search?hl=en&client=firefox-a&hs=l0R&rls=org.mozilla:en-US:official&ei=gHymS9KaJJuy0gSgsKzxCQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAQQBSgA&q=installing+doom+3+ubuntu&spell=1")" in google will show you some more too.
yeah I saw those but haven't the foggiest idea what that means... do I have download the entire game? Not sure...

---

### Post by darthmob on 2010-03-21
Did you even click the links? There are step-by-step instructions on how to install it. It can't get any simpler. Btw, you only have to download the binaries and all other files will be installed from the disks.

---

### Post by bigseb on 2010-03-21
> **darthmob said:**
> Did you even click the links? There are step-by-step instructions on how to install it. It can't get any simpler. Btw, you only have to download the binaries and all other files will be installed from the disks.
yes I clicked them... I see mountains of code that I don't understand and don't know what to do with. Anyway it wouldn't install properly from the discs as I mentioned above. Help me out here I'm new to all this....

---

### Post by Ferrat on 2010-03-21
> **bigseb said:**
> yes I clicked them... I see mountains of code that I don't understand and don't know what to do with. Anyway it wouldn't install properly from the discs as I mentioned above. Help me out here I'm new to all this....

Code? 
It's step by step howto if you just read it, there is no code?

---

### Post by bigseb on 2010-03-22
**Acquiring Doom3 for Linux**

 You can download the latest version from [id Software's ftp server]("ftp://ftp.idsoftware.com/idstuff/doom3/linux/") As of 2008-03-19, the latest version is doom3-linux-1.3.1.1304.x86.run. 
This package contains only the binary sources for Linux! 
 
**Installation of the Linux binary**

 The installation writes to /usr/local/games/doom3 by default. You should install using sudo to ensure write permissions to /usr/local/games/doom3, and make sure that the installation file is executable. 
chmod +x doom3-linux-x.x.xxxx.x86.run
sudo ./doom3-linux-x.x.xxxx.x86.run

# As of 2008-03-19 this is:
sudo ./doom3-linux-1.3.1.1304.x86.run 
**Add the missing files**

 The following files need to be copied from the win32 install CDs to your base/ directory. by default, /usr/local/games/doom3/base 
base/pak000.pk4
base/pak001.pk4
base/pak002.pk4
base/pak003.pk4
base/pak004.pk4

# On Ubuntu 7.04, you can find these by inserting discs 1-3 one-after-the-other
# and then doing, for each disk:
sudo cp /media/cdrom0/Setup/Data/base/pak00*.pk4 /usr/local/games/doom3/base




^^^ I copy/pasted this from the first link (just as an example). For starters there 
is no mention of whether or not to use my own discs. Must I download the entire 
game? How legal is  that?

When I click on that first link a page opens with three links. If I click on the 
link of the recommended file it opens a page with tons of what I call code. I don't 
know what to do with that...

Again, I'm a Linux beginner. What might obvious to you isn't that obvious to me.

---

### Post by Toffeeapple on 2010-03-22
> **bigseb said:**
> For starters there is no mention of whether or not to use my own discs.

ah! but there is....

> The following files need to be copied from the win32 install CDs to your base/ directory. by default, /usr/local/games/doom3/base
base/pak000.pk4
base/pak001.pk4
base/pak002.pk4
base/pak003.pk4
base/pak004.pk4

# On Ubuntu 7.04, you can find these by inserting discs 1-3 one-after-the-other
# and then doing, for each disk:
sudo cp /media/cdrom0/Setup/Data/base/pak00*.pk4 /usr/local/games/doom3/base

win32 install CDs = Your original game disks. Look in the CDs and you will see, read the how too and you will learn and know.. : )

> **bigseb said:**
> Must I download the entire game?

No..

> You can download the latest version from id Software's ftp server As of 2008-03-19, the latest version is doom3-linux-1.3.1.1304.x86.run.
This package contains only the binary sources for Linux!

> **bigseb said:**
> How legal is that?

Perfectly legal, they are happily distributing their own stuff from their own servers.

Unfortunately there isn't a one click and it's done answer. My suggestion to you would be to read the how to [here]("https://help.ubuntu.com/community/Doom3"), follow it step by step, just do it and if you make a mistake it wont be the end of the world and you will learn something as you do it and eventually if you keep trying it will happen.

Good luck.

---

### Post by bigseb on 2010-03-22
Thanks toffeeapple, I'll give it a shot. You know, having been a windows user my entire life makes this a rather daunting task.

---

### Post by Toffeeapple on 2010-03-22
> **bigseb said:**
> Thanks toffeeapple, I'll give it a shot. You know, having been a windows user my entire life makes this a rather daunting task.

I was in the same situation three years ago : )

---

### Post by bigseb on 2010-03-23
IT WORKS!

Sounds jerks occasionally, but only in cut scenes. Hurrah!

Major reps to Toffeeapple!!

---

### Post by Brebs on 2010-03-24
> **bigseb said:**
> Sounds jerks occasionally, but only in cut scenes.
See [other doom3 thread](http://ubuntuforums.org/showthread.php?t=1304228).

---

