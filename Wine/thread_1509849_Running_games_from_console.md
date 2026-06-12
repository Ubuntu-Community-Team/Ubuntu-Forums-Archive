---
title: "Running games from console"
date: 2010-06-14
forum: Wine
---

### Post by Zireth ZH on 2010-06-14
Hey all i wanna know how to run my wine games from console n order to get the error outputs.. my games are crashing after mins of running ... if anybody knows whats the prob please help me out... but well main thing is how do i run the games from console?

This is where the game is located at... 
/home/backstage/.wine/drive_c/Perfect World Entertainment/Ether Saga Online/element/

Problem is when i try to point the location with *cd* in the console it gives me an error saying no such file in directory .. i can point to *drive_c* but not any far...

Please help thanks

---

### Post by Soulcage on 2010-06-15
I don't have eso, but if I were to run say war3 I would use:
```
cd ~/.wine/drive_c/Program\ Files/Warcraft\ III/ && wine Frozen\ Throne.exe
``` You may even want to add -windowed or run in a virtual desktop.

---

### Post by cogadh on 2010-06-15
The terminal doesn't recognize the spaces in the directory names, so when you use the "cd" command, you need to add escape characters (the "\") to allow the terminal to "see" the spaces:
```
cd /home/backstage/.wine/drive_c/Perfect\ World\ Entertainment/Ether\ Saga\ Online/element/
```

---

### Post by Zireth ZH on 2010-06-15
thanks alot guys for the help and the extra info provided

---

