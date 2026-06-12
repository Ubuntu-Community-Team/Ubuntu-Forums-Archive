---
title: "wine alt+f4 problem"
date: 2010-10-19
forum: Wine
---

### Post by LifeEnemy on 2010-10-19
I just installed microsoft office on my ubuntu laptop 10.04 via WINE. It seems to be working pretty well after a reinstall, but I'm still having trouble closing the windows. I can't close any MS office program with alt+f4, or any other method (right click menu, middle click on cairo-dock icons, Compiz scale addon, etc) except using the X button within the app or going through the menus. It's very frustrating when I don't have a mouse plugged into my laptop. I can't find any other mention of this problem around the net. Please help.

Thanks in advance!

---

### Post by LifeEnemy on 2010-10-19
[https://help.ubuntu.com/community/Wine#Creating file associations](https://help.ubuntu.com/community/Wine#Creating file associations)

Problem 2:
I'm also having trouble creating file associations (opening MS Word when clicking .doc files, for example). I followed the guide on the Wine page on the wiki, but nothing. I currently have a script set up:

>  #!/bin/sh

QUICKPARLOCATION="c:\\Program\ Files\\"Microsoft\ Office"\\Office12\\WINWORD.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

But when I run the command they suggest to make sure it works nothing happens:

> chmod +x ~/.wine/WINWORD

Any suggestions?


EDIT: I've also tried changing the QUICKPARLOCATION using quotes around the folders with space in the name, and with/without the "\" before spaces in their names.

---

### Post by LifeEnemy on 2010-10-20
bump

---

### Post by alexandari on 2010-10-20
```
wineserver -k 
```

---

### Post by LifeEnemy on 2010-10-20
I put that into a terminal but it didn't do anything. Am I supposed to put that into the script somewhere? Which problem is that supposed to help? Sorry if I'm not getting something obvious, I'm not good with code and such.

---

### Post by alexandari on 2010-10-20
Alt+f2  --> wineserver -k

or yes,in the terminal. should close all wine stuff opened

---

### Post by LifeEnemy on 2010-10-20
WEll, that is helpful some, but I can already close the windows by clicking on the X in the corner. The problem is that there's no easy way to do that without a mouse. I use the scale compiz plugin a lot and I can't close windows in it when alt+f4 doesn't work. Thanks for the tip, though. Do you know of any way I could get alt+f4 working?

---

### Post by LifeEnemy on 2010-10-22
bump. Lookin for some way to alt+f4 out of my MS office WINE apps.

---

### Post by LifeEnemy on 2010-10-23
bump. Can anyone help me with my file association problem too?

---

### Post by LifeEnemy on 2010-10-25
bump

---

### Post by Verbeck on 2010-10-25
try running wine in a virtual desktop
to do that, open configure wine>Graphics tab and check emulate a virtual desktop
you can change the desktop size from there

---

### Post by katykat on 2010-10-25
> **LifeEnemy said:**
> bump

Since you are not using a mouse, to try to perform a mouse function will always be clunky. 

A simple solution would be to hotkey a batch script on your desktop where alt-4 calls pkill winword, or whetever it is called in ps aux. 

As to wine associations, do a google for TORRENT ASSOCIATE UTORRENT WINE.
It deals with some issues involving file associatioons with wine and utorrent that maybe helpful.

Ideally you should be able to right click on a DOC file and do a filesearch for Word and have it stick.

---

### Post by LifeEnemy on 2010-10-26
> **Verbeck said:**
> try running wine in a virtual desktop
to do that, open configure wine>Graphics tab and check emulate a virtual desktop
you can change the desktop size from there

The virtual desktop seems to works ok. Alt+f4 works and other window functions. I don't like how it keeps all the WINE apps open in a single window. Is there any way to open a desktop for each document I open? Or something with the same effect.


I managed to get file associations working by playing with settings. I don't know anything about "batch scripts" but hopefully I won't need it.

THanks for all the help so far guys!

---

### Post by LifeEnemy on 2010-10-31
bump. Also having trouble resizing the WINE window. It doesn't change the size of the document in the window, which either cuts off some of the document or shows weird artifacts to fill in the "blank" space.

---

### Post by uRock on 2010-10-31
Moved to Wine sub-forum.

---

### Post by LifeEnemy on 2010-10-31
thanks!

---

### Post by LifeEnemy on 2010-11-02
bump

---

### Post by LifeEnemy on 2010-11-04
bump

---

### Post by uRock on 2010-11-04
Have you asked your question here? [http://forum.winehq.org/](http://forum.winehq.org/)

---

### Post by LifeEnemy on 2010-11-10
I just posted it there. fingers crossed.

---

