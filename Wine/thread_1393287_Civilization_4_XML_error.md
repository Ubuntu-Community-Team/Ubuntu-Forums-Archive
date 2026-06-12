---
title: "Civilization 4 XML error"
date: 2010-01-29
forum: Wine
---

### Post by charkoal on 2010-01-29
This game Has installed no problems but when I go to play the game it opens up and goes to loading screen then i get the XML error message pop-up twice then the game closes.

"Error locating tag node in SetGlobalClassInfo function Current XML file is: GameInfo/CIV4PlayerOptionInfos.xml"

Any help to fix this problem will be appreciated thanks.

---

### Post by charkoal on 2010-01-30
I've tried restarting comp, didn't fix it :(

---

### Post by brian70809 on 2010-01-30
In the wine config. you need to select Civ4...

Go to Libraries and seleect Add.
Select msxml3(native)

Hit OK..

It should work after that.

Good Luck!

---

### Post by edemark on 2010-02-04
Hi 
NB1 restarting your pc does not really helps in linux (unless you have just installed a new kernel) but certainly not for a game.
NB2 there is a command, which i have never used though, called wineboot which emulates the restart of the w i n d o w s machine.

So about your question I would suggest using winetricks to get missing libs (d l l) please have a look on this site 
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
also would suggest to have a look on wine's appdb
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514)
and see what you are missing depending of the civ iv  version you have.

good luck 

> **charkoal said:**
> I've tried restarting comp, didn't fix it :(

---

### Post by Piteco on 2012-02-06
> **brian70809 said:**
> In the wine config. you need to select Civ4...

Go to Libraries and seleect Add.
Select msxml3(native)

Hit OK..

It should work after that.

Good Luck!

I was having the exact same problem and this worked fine for me. 

Thx Brian

---

