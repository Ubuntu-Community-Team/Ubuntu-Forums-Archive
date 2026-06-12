---
title: "Editing the target of a shortcut to an EXE file"
date: 2011-02-26
forum: Wine
---

### Post by cymbaline42 on 2011-02-26
I've installed Call of Duty 1 using Wine in a folder under /Documents/Games/Call of Duty.  

In order to enable cheats, I am supposed to add the following *"+set thereisacow 1337 +set developer 1 +set sv_cheats 1 +set monkeytoy 0"* to the end of the target in the shortcut to the game.  

I tried creating a launcher on the desktop and added the above line to the end of the Command but I get an error saying **"Couldn't load default.cfg.  Make sure CoD is run from the correct folder"**

I copied the entire contents of the CoD folder to .wine/Program Files/Call of Duty/  but to no avail.  I'm still getting the error.

Any suggestions?  Thanks in advance.

---

### Post by cymbaline42 on 2011-02-27
Okay, I figured out how to enable cheats while running CoD 1 on Wine.  It's pretty simple really, can't believe I didn't try this before posting <sheepish look>

Instead of double clicking codsp.exe to start the game, open the terminal, go to the directory where codsp.exe is located, and start the game by typing "./codsp.exe +set thereisacow 1337 +set developer 1 +set sv_cheats 1 +set monkeytoy 0"

The cheats will be enabled now, and you can access the console by pressing tilde (~) during the game and enter whichever code you want to.  Cheers.

---

### Post by 10minuteaccount on 2011-03-07
You could create a shortcut/launcher as well, like I did for my Svenska Spels Poker client... This would save you the hassle of starting it manually with those parameters each time. :)

Here's what I run to start my poker client;

```
wine start /Unix /home/username/.wine/drive_c/Program\ Files/Svenska\ Spels\ Poker/poker.exe
```

It should work to just add the other parameters directly after (in proper Unix format) i.e.:

```
wine start /Unix /home/username/.wine/drive_c/Program\ Files/Svenska\ Spels\ Poker/poker.exe\ +set\ thereisacow\ 1337\ +set\ developer\ 1\ +set\ sv_cheats\ 1\ +set\ monkeytoy\ 0
```

...and so on.

This should automatically use the proper working directory for the program, thus including all required dll libraries etc.

Or you could use your own solution in a shell script and run that  from the launcher instead. :)

e.g.
```
#!/bin/bash
cd /home/username/.wine/drive_c/Program\ Files/Call\ of\ Duty/
wine codsp.exe\ +set\ thereisacow\ 1337\ +set\ developer\ 1\ +set\ sv_cheats\ 1\ +set\ monkeytoy\ 0
```
Save it somewhere as cod.sh and run it to start the game.

---

