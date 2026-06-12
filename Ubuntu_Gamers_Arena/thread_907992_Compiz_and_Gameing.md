---
title: "Compiz and Gameing"
date: 2008-09-02
forum: Ubuntu Gamers Arena
---

### Post by senectus on 2008-09-02
Does anyone know if there is a nice neat slick way to have Compiz on your desktop all the time, but either automatically turn it off when you launch a game or have it not greatly affect game performance when you're running a game...?

I've got a LAN coming up and all the other guys are still stuck with Windows.. I'd love to show them up with Compiz, but not at the huge cost of performance I saw the last time I tried it...

---

### Post by Sef on 2008-09-05
Get more ram possibly.  How much do you have?

---

### Post by senectus on 2008-09-05
> **Sef said:**
> Get more ram possibly.  How much do you have?

1gb :-/

Actually its been a while since I've tried compiz + games at the same time... It's performing a _lot_ better now.. its not so bad.

---

### Post by NilsHG on 2008-09-05
```
sudo apt-get install fusion-icon
```
when you run fusion icon, it sits in your tray and you can click it to simply turn compiz on and off. 

another way is to create a simple starter script as game launcher, which automatically turns of compiz, starts the game and restarts compiz when the game closes. 

try searching for those if you do not know how to write them yourself.
gl and have fun at your LAN

(offtopic, what kind of games do you play with your friends and their windows machines, or do you dualboot for gaming?)

---

### Post by Cresho on 2008-09-05
i HAVE ONE!

create a folder in your home and call it custom stuff or what ever you want.  In this folder create a file called game.sh  now right click and go to properties and select permission and allow as executable.

paste this into it.

#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
#run game;
cd ~/Installed_Programs/etqw
sleep 1 && ./etqw;

#Compiz on;
compiz --replace &
metacity --replace &






save the file.

this one is for my enemy territory quake wars.  if you need to really customize it, post here or pm me and ill give you an answer.  I have around 30 plus customizations which also include wine games like anachronox or what ever.

what this does is disables compiz, runs game.  after you close game, compiz re-enables like magic.

after you have the sh file working, test it by double clicking on it or in start menu, right click and select icon or create a new one and direct this file as the executable instead of the actual game.

---

### Post by ad_267 on 2008-09-05
I wrote a pretty basic script that does this here: [http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)

It works for any game, you just have to put the script in your path and change the commands in your menu by putting "playgame" in front. I'm actually using Metacity at the moment so just commented out the lines that replace compiz and metacity.

---

### Post by senectus on 2008-09-05
> **NilsHG said:**
> ```
sudo apt-get install fusion-icon
```
when you run fusion icon, it sits in your tray and you can click it to simply turn compiz on and off. 

another way is to create a simple starter script as game launcher, which automatically turns of compiz, starts the game and restarts compiz when the game closes. 

try searching for those if you do not know how to write them yourself.
gl and have fun at your LAN

(offtopic, what kind of games do you play with your friends and their windows machines, or do you dualboot for gaming?)

Sounds perfect, will give it a go when I get home.

I _refuse_ to use windows at home, so no dual boot.
We play Quake 4, UT2004, Doom3, Quake 3, NWN, Serious Sam 2, ET:QW...
I hear the guys are going to want to play CnC3 so I may have to break out the WINE.

I tend to prefer single player games so I don't have that big a range.

---

