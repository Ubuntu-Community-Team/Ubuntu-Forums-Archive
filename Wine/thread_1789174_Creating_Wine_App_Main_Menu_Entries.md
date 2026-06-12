---
title: "Creating Wine App Main Menu Entries"
date: 2011-06-23
forum: Wine
---

### Post by linuxyogi on 2011-06-23
Hi,

I am playing Tom Clancy's Hawx (Game) using wine ver 1.3.22

When I click on the exe in the installation folder the game plays fine but when I click on the 

main menu entry which I created using alacarte the Game hangs after the intro video.

This is how I created the menu entry 

```
"wine /path to exe" 
```Then created a script 

```
#! /bin/bash
wine /home/linuxyogi/.Tom\ Clancy\'s\ H.A.W.X/HAWX.exe

```and tried pointing to that script in alacarte but same thing, game hangs right after the 

intro video ends.

What is going wrong ?

---

### Post by VigneshChennai on 2011-06-23
Try this :

wine start /unix <path to exe>

Example. if exe file is in /opt/app.exe

then
>  wine start /unix /opt/app.exe

---

### Post by linuxyogi on 2011-06-23
> **VigneshChennai said:**
> Try this :

wine start /unix <path to exe>

Example. if exe file is in /opt/app.exe

then

Worked !!! Thanks  :D

---

### Post by tzesku on 2013-04-26
For those of you who want to creat new menu entry for wine installed games and aplications the right command should be :

sh -c "cd /home/USER/PATH\ TO\ EXE\ FILE\ ; wine Executable_File.exe"

---

