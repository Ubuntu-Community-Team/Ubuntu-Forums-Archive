---
title: "call of duty 4 black screen and multiplayer not working"
date: 2011-04-24
forum: Wine
---

### Post by friendleo on 2011-04-24
Hey guys my call of duty game that I installed is not working I have to keep troubleshooting it to get it on and when I have it on the game runs really slow like slides 1by1

specs: nvidia graphics
amd sempron si-42

---

### Post by Perfect Storm on 2011-04-24
Moved to UF wine forum.

---

### Post by Claus7 on 2011-04-24
Hello,

2 quick things:
1) open the setup of the program and choose a resolution you would like the wine window  of the game to have.
2) go to wine configuration and choose the same resolution to exist while opening wine programs.

Regards!

---

### Post by friendleo on 2011-04-24
yeah i know all that but how do I change the resolution? and fix the black screen?

---

### Post by Claus7 on 2011-04-24
Hello,

first of welcome to the forums! At the time I did not have a lot of time available.

Now, concerning your problem:

1) Go to: applications->Wine->Configure Wine
and choose the tab graphics.
There tick the "emulate virtual desktop option" and choose a resolution lower than that of your screen (800x600 for start would be nice)
2) Go to: applications->Wine->Browse C: Drive, and navigate to the directory where Call of Duty is installed. Find the setup.exe file and open it either by double clicking on it, or navigate via terminal and open it via the command:
```
wine setup.exe
```
and choose again the resolution 800x600.

Does your game play that way?
It might be that you have to fix some other options concerning visuals. Usually, when you have sound, yet black screen, you have to tamper with resolution issues, for your game to be displayed correctly.

Regards!

---

