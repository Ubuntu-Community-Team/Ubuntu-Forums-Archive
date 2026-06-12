---
title: "Call of Duty 4 and wine 1.1.17"
date: 2009-03-28
forum: Wine
---

### Post by Diblic on 2009-03-28
Hey everyone

So my problem is that when I try and run Call of Duty 4 on Wine 1.1.17 (Using Ubuntu 8.10) it does not run full screen, instead it leaves my Avant window manager on the bottom and my task bar at the top visible. (For example I cannot click "apply" when changing settings in CoD because the Avant in on the way) Here is a picture for reference [http://tinypic.com/view.php?pic=24d0weu&s=5](http://tinypic.com/view.php?pic=24d0weu&s=5) . 

My question is, that what can I do to run it fullscreen?

I am completely new to Linux, been using Ubuntu for like a week now, so please consider that in your answer :D

Best regards and thanks in advance!

-Diblic-

---

### Post by asda__ on 2009-03-29
Just go to Wine settings (Terminal > winecfg) and there, in the "Graphics" tab, uncheck "Allow the window manager to decorate windows".

---

### Post by Diblic on 2009-03-30
That did not work, the menus are still there :(

---

### Post by Stunts on 2009-03-30
Hello!
Try to turn of compiz and replace it with metacity.
just press "Alt+F2" and type:
```

metacity --replace

```

Wine doesn't play well with compiz.
After you are done playing you can turn the desktop effects back on by doing the opposite in "Alt+F2":
```

compiz --replace

```

This should at least make the menu bar go away. as for AWN, well, Maybe try an auto hide function?
Good luck!

---

### Post by Diblic on 2009-03-30
Found a solution, I unchecked both, "allow window manager to decorate windows" and "allow window manager to control windows" and now its running all good and full screen. ;D

---

### Post by Stunts on 2009-03-30
Glad to hear that!
Have fun!

---

### Post by Diblic on 2009-03-30
Hmm,

now I have to get Garena running but thats completely another story...

:D

---

### Post by Stunts on 2009-03-30
Try the winehq appdb.
It's a great resource for that sort of thing.
Good luck once again.

---

### Post by x3|rAGE on 2009-04-01
Diblic, I ran into the same problem but I found a solution for keeping "allow window manager to decorate windows" and "allow window manager to control windows" enabled. Deactivate them and then go into your game. Adjust your game resolution to match your desktop's resolution. Go back into wine settings and enable "allow window manager to decorate windows" and "allow window manager to control windows" and you should be able to use desktop effects, most notably the cube, while the game is running. :)

---

### Post by Dale Lewis on 2009-07-23
Hi folks...Hope I am in the right place and not hijacking this thread. I have COD 4 running under the git version of wine  `1.1.26 on Juanty 64 bit. The games runs great while loading but when you enter game play from the menu and you select your mission it will load and the graphics will turn white to the point it's not playable. My graphics card is an Nvidia 9400 with a gig of ram...any ideas on why that could be happening? Thanks!!!!!!

---

### Post by Stunts on 2009-07-24
Something similar happens when playing warcraft3 and switching application/desktop.
On war3 activating the option "emulate a virtual desktop" solves that issue. Maybe you can try something similar?
try running it like this:
```
[FONT=monospace]
[/FONT]wine explorer /desktop=0,1280x1024 "path_to_call_of_duty4.exe"[FONT=Verdana][/FONT]
```
Where you replace 1280x1024 for your full screen resolution. (and of course enter the correct path between the quotes).

Good luck.

---

### Post by Dale Lewis on 2009-07-24
Tried to no avail...I can't find any additional info on this issue either. Thanks!!

---

### Post by Dale Lewis on 2009-07-25
Needed to match screen depth...that corrected it!

---

### Post by Stunts on 2009-07-25
Glad you got it to work. =-)

---

