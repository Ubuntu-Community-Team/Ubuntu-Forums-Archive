---
title: "Help me with a script/Prank please"
date: 2009-04-01
forum: The Cafe
---

### Post by Ms_Angel_D on 2009-04-01
I have an Idea, a little prank I want to play on the hubby, but I don't know jack about scripting. I want to set it up so when he clicks his guild wars Icon it will pop up with some kind of April Fools message instead of running the game, can anybody help me?

Thanks,
Angel

[Edit]
Guess I should have said it's on His Ubuntu I want to do this
[/Edit]

---

### Post by smartboyathome on 2009-04-01
Is it on Windows or Linux?

---

### Post by Ms_Angel_D on 2009-04-01
Ohh Sorry It's on Ubuntu ;)

---

### Post by smartboyathome on 2009-04-01
Install Zenity using Synaptic. Then edit the command (make sure to save it!!!) in the menu by right clicking on the menu and clicking edit. For the command, use this:

zenity --warning --text='Insert text here.'

---

### Post by Ms_Angel_D on 2009-04-01
Sweet thanks :D

---

### Post by steeleyuk on 2009-04-01
Zenity should be installed by default.

```
#!/usr/bin/env bash

zenity --error --text="Tough luck, game is deleted";
sleep 3
zenity --error --text="April fool's!"
```

This one will wait three seconds before displaying the April Fool's message.

---

### Post by Ms_Angel_D on 2009-04-01
> **steeleyuk said:**
> Zenity should be installed by default.

```
#!/usr/bin/env bash

zenity --error --text="Tough luck, game is deleted";
sleep 3
zenity --error --text="April fool's!"
```

This one will wait three seconds before displaying the April Fool's message.

lol that's even better :D

---

### Post by woppy71 on 2009-04-01
Naughty you! ;)

---

### Post by dbbolton on 2009-04-01
Here's a suggestion. Make a file called slooflirpa.sh and put this in it:

```
[FONT=monospace]
[/FONT]#!/bin/bash
zenity --error \
          --text="Critical Error: 0 Guild Wars PK3 files found!"

```

Right click on the file, go to properties, permissions, and choose "allow execution as a program" or whatever it says in your file manager.

Put what ever you want in the quotes. Now, if the Guild Wars Icon is on the desktop, make a copy of it, and move one of the copies somewhere else. Now open it with a text editor and edit this line

```

Exec=/path/to/slooflirpa.sh

```

except obviously adding the actual path to the file.

If the icon is in the Gnome menu, go to System > Preferences > Main menu, find the icon, right click on it, choose properties, and change the command to the path to the slooflirpa.sh file.

If the icon is on the gnome panel, just right click on it, choose properties, and do as above.

If he's using KDE, I can't help you :D

---

### Post by Ms_Angel_D on 2009-04-01
> **woppy71 said:**
> Naughty you! ;)

lol


Quick question how do I make the shell script run without asking me if I want to run in terminal, display or run?

---

### Post by steeleyuk on 2009-04-01
Easiest way is to create a launcher, by right clicking on the desktop, and linking to the shell script.

---

### Post by Ms_Angel_D on 2009-04-01
Ok I got it set up, now I just gotta wait until 3:00 P.M. when he get's home....lol

Thanks a bunch guys :D

---

### Post by MysticGold04 on 2009-04-01
> **MetalHellsAngel said:**
> Ok I got it set up, now I just gotta wait until 3:00 P.M. when he get's home....lol

Thanks a bunch guys :D

Wow, thats mean! :mrgreen:

---

### Post by Dragonbite on 2009-04-01
Let us know how he takes it.. better yet record it on a webcam or something!

Slow motion his face twisting in agony for full effect!!

---

### Post by BGFG on 2009-04-01
These are the kind of projects that really bring our community together :P now who else can we nail ?

---

### Post by Mehashi on 2009-04-01
Hee Hee!

I like the thought! I know a boy to try this on, he thinks his ubuntu is so much better than mine!

*plans to get time alone with his system...*

I hope it went well! 
(Although it would be even funnier if it didn't) - after joke :
YOU: "don't worry I saved the proper file for you"
HIM: "thank god! You had me scared!"
YOU: "Haha no don't worry"
you find the file and click on it...
the same joke file pops up again...
YOU: "Oh... Er... Um...sorry?"
HA! Nothing is funnier than a joke gone wrong!

I must avoid doing that!
I Hope he laughed anyway!
^_^

---

### Post by steeleyuk on 2009-04-01
Wow, another girl using Ubuntu. April Fool's again?! :p

---

### Post by billgoldberg on 2009-04-01
> **steeleyuk said:**
> Easiest way is to create a launcher, by right clicking on the desktop, and linking to the shell script.

Which is of course a huge security flaw in Gnome (kde has something similar if I remember correctly).

---

### Post by steeleyuk on 2009-04-01
How so?

---

### Post by BGFG on 2009-04-01
> **MetalHellsAngel said:**
> Ok I got it set up, now I just gotta wait until 3:00 P.M. when he get's home....lol

Thanks a bunch guys :D

Did you get him ?

---

### Post by Mehashi on 2009-04-01
Maybe it didn't go right!

maybe she is trying to console (sp?) him!
 
I hope it went ok!

---

### Post by Ms_Angel_D on 2009-04-01
He's not home yet it's only 2:00 P.M. Here It was 8:00 A.M. when I started this thread...don't worry though I'll keep you posted ;)

---

### Post by sisco311 on 2009-04-01
> **billgoldberg said:**
> Which is of course a huge security flaw in Gnome (kde has something similar if I remember correctly).

and in the terminal.

> **steeleyuk said:**
> How so?

you can run a script without execute permission.

---

### Post by billgoldberg on 2009-04-01
> **steeleyuk said:**
> How so?

I presume that was meant for me.

Well you can kind of guess why.

Using the desktop launcher feature in Gnome, scripts can be executed without the proper rights and without prompts.

This can become a serious problem if Ubuntu becomes more mainstream, together with .bashrc and I'm sure there are some other holes.

---

### Post by steeleyuk on 2009-04-01
Unless the execute bit is set on my machine, it throws up an error saying "Permission Denied", "Could not execute" (or words to that effect).

---

### Post by sisco311 on 2009-04-01
> **steeleyuk said:**
> Unless the execute bit is set on my machine, it throws up an error saying "Permission Denied", "Could not execute" (or words to that effect).

that's because you don't know how to create the launcher. :evil:

you have to specify the interpreter:
```
bash path/to/file
python path/to/file
...

```

EDIT: the file is not executed, it's interpreted by bash, python...

---

### Post by steeleyuk on 2009-04-01
Well, that looks to me an unfortunate side effect of having read permissions. ;)

---

### Post by billgoldberg on 2009-04-01
> **steeleyuk said:**
> Well, that looks to me an unfortunate side effect of having read permissions. ;)

No, that's a huge security risk.

---

### Post by steeleyuk on 2009-04-01
Is there a bug filed against it then?

I can't see a way that would solve it directly from GNOME/KDE. The only way I can think of is patching Python/Bash to only allow interpretation of code from files with execute bits. Then again, there's got to be a downside to that or something that means it just won't work like that (PS. I'm no developer).

Edit: just reading on Slashdot, noticed the comment 'Expected behaviour'.

---

### Post by mcduck on 2009-04-01
> **steeleyuk said:**
> Is there a bug filed against it then?

I can't see a way that would solve it directly from GNOME/KDE. The only way I can think of is patching Python/Bash to only allow interpretation of code from files with execute bits. Then again, there's got to be a downside to that or something that means it just won't work like that (PS. I'm no developer).

Edit: just reading on Slashdot, noticed the comment 'Expected behaviour'.

You could still use cat to read the code from any text file and redirect it to the command interpreter..

I don't see that as a bug as you need to be the user who's desktop setup you are messing with, or root, to do anything and at that point it definitely isn't a question of security but of bad system administration. :D

---

### Post by dbbolton on 2009-04-01
> **steeleyuk said:**
> Is there a bug filed against it then?

I can't see a way that would solve it directly from GNOME/KDE. The only way I can think of is patching Python/Bash to only allow interpretation of code from files with execute bits. Then again, there's got to be a downside to that or something that means it just won't work like that (PS. I'm no developer).

Edit: just reading on Slashdot, noticed the comment 'Expected behaviour'.
Hey, I'm named after your location :lol:

---

### Post by Ms_Angel_D on 2009-04-01
roflmao He was like WTF is going on with my guild wars, I changed the sleep from 3 seconds to 5.. Then I started laughing and he was like YOU B***CH and started laughing to.....lol it was pretty funny, Thanks guys ;)

---

### Post by tarahmarie on 2009-04-01
> **steeleyuk said:**
> Wow, another girl using Ubuntu. April Fool's again?! :p

Am girl and use *K*ubuntu!

NOT an April Fools!

---

### Post by tarahmarie on 2009-04-01
> **MetalHellsAngel said:**
> roflmao He was like WTF is going on with my guild wars, I changed the sleep from 3 seconds to 5.. Then I started laughing and he was like YOU B***CH and started laughing to.....lol it was pretty funny, Thanks guys ;)

That was an AWESOME prank. L*E*G*E*N*D*A*R*Y props.

---

### Post by Mehashi on 2009-04-01
That's great! I am glad it went well for you!

Definately going to have to do this to my friend!
[COLOR=Magenta]
^_^[/COLOR]

---

