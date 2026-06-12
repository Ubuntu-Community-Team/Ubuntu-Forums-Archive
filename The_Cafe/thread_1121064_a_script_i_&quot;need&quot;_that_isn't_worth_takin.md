---
title: "a script i &quot;need&quot; that isn't worth taking to developers section"
date: 2009-04-09
forum: The Cafe
---

### Post by chriskin on 2009-04-09
i've been playing urban terror a lot lately, yet it doesn't really play nice with compiz, so i have to close compiz every time
i want to make a script that 1)puts metacity instead of compiz 2)closes cairo-dock 3)closes screenlets 
and another to make then run again :)

the only problem is, i have absolutely no idea of scripting :)

:p

---

### Post by joshdudeha on 2009-04-09
It's been a while since I've been in ubuntu.
But couldn't you make buttons, maybe placed in the task bar, that kill these processes via a command.
It should be fairly easy to do.
Just make a new custom button on the panel, enter the commands, and click them when you need to.

And with the metacity thing, I can't remember the command, is it "metacity replace" ? idk.
Ask someone :D But it should work this way.

---

### Post by chriskin on 2009-04-09
> **joshdudeha said:**
> It's been a while since I've been in ubuntu.
But couldn't you make buttons, maybe placed in the task bar, that kill these processes via a command.
It should be fairly easy to do.
Just make a new custom button on the panel, enter the commands, and click them when you need to.

will the commands be something just like "kill x" ?

---

### Post by ajgreeny on 2009-04-09
No idea about cairo-dock, but to kill compiz and run a program, then start compiz again it's simple, so it should be simple to add cairo dock and screenlets commands as well to the script.  In a text editor type
```
#!/bin/bash
metacity --replace & killall cairo-dock & killall screenlets & urban-terror-command  && compiz --replace && cairo-dock & screenlets
```I don't know the commands for screenlets or cairo-dock so change those as needed. Save it as **urban-terror.sh** in your home and make it executable in terminal with ```
chmod +x urban-terror.sh
``` or using nautilus, right click on the file, properties>permissions tab.  Now make a launcher on your desktop called **Urban-terror** with the command box as ```
/home/username/urban-terror.sh
```

---

### Post by chriskin on 2009-04-10
this works almost perfect :)

thank you :) 
the only problem is that it opens thescreenlet manager as well but it is ok :)

thanks :)

:guitar:

---

### Post by Sealbhach on 2009-04-10
I use the Compiz Fusion Icon to switch from Compiz to Metacity before I go playing games.

It's in the repos.

.

---

### Post by chriskin on 2009-04-10
yes of course but with the script given by ajgreeny i can just double click and get compiz turned into metacity, the game will start and when i quit the game, metacity will leave the room for compiz once more :)

---

### Post by Sealbhach on 2009-04-10
> **chriskin said:**
> yes of course but with the script given by ajgreeny i can just double click and get compiz turned into metacity, the game will start and when i quit the game, metacity will leave the room for compiz once more :)

Oh, OK, that's neat, I think I'll try it.


.

---

### Post by OffHand on 2009-04-10
I made this one:

[http://ubuntuforums.org/showthread.php?t=489341](http://ubuntuforums.org/showthread.php?t=489341)

---

### Post by ajgreeny on 2009-04-10
There is actually a script available from forlong [Compiz-switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch") which I also use to turn compiz on and off alternately with a single click (I have my whole system set to single clicks, as that's the way I prefer it), but I was just playing with script writing when I did this script to turn it off then on again, etc etc.  If I had used compiz-switch in the script it would reverse the situation if compiz was already off when I used the script; not what was wanted at all.

As regards the screenlets manager starting, I suspect you need to make sure you get the correct command for screenlets in the script.  I've never used them so have no idea what it would be, but I'm sure there must be a way to get them running without the manager as well.

---

