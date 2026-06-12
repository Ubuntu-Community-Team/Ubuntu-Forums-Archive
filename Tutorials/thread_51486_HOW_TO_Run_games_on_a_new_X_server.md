---
title: "HOW TO: Run games on a new X server"
date: 2005-07-24
forum: Tutorials
---

### Post by endy on 2005-07-24
I already covered this in an unrelated post in the gaming forum and the nuts and bolts of this are all probably in the [linux-gamers.net](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=43) how to, but I like to keep things local here :)

Basically the ideas behind this is you run can run your games like Doom 3, Quake, Enemy Territory and pretty much anything in a new X server. The main benifit of this is that your dektop will get backgrounded which should give the game a performance boost and the ability to switch between your fullscreen game and your desktop, for example to check on an irc message.

I found this incredibly useful while clan gaming in the past as people would message me alot in irc while I played and otherwise I had to quit the game to see what it was. And now even though I don't play seriously any more I can't live without it. I will be using Enemy Territory as the example as it's my favorite game :)

"Enough already, show me the stuff" I hear you say, well ok then here you go:


1. First to allow you to run a new X display you need to edit the "/etc/X11/Xwrapper.config" file:

```

sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo su
md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
exit
sudo dpkg-reconfigure xserver-common


```Then  make sure you change the first option to "Anybody" and hit enter twice.


2. Next we have to set your ~/.Xauthority file up. This may look tricky but it's very straight forward, all you need to do is add a line using a special key we find. So, in a terminal type:

```

xauth
list

```And you should get an output something like this:

```

ananke/unix:0  MIT-MAGIC-COOKIE-1  **9fde426e5g03b20f4b7e51cb329d3033**
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  **9fde426e5g03b20f4b7e51cb329d3033**

```Yours WILL be different, thats ok. Now we need to add a new line and then exit to save it. So we type in "add :1.0 MIT-MAGIC-COOKIE-1" followed by that long alpha numeric string. I've highlighted mine in bold above so you know what I'm talking about but remember to use yours. So for me I would type the following:

```

add :1.0 MIT-MAGIC-COOKIE-1 9fde426e5g03b20f4b7e51cb329d3033
exit

```Remember YOU have to use YOUR OWN sting of numbers and letters copied form the output we got earlier, mine is just an example. Ok? I know it's a bit abstract but hopefully this is clear enough.


3. Create the script "x.et":

```

gedit x.et

```And paste the following:

```

#!/bin/bash
xinit /usr/local/games/enemy-territory/et $* -- :1

```


4. Now we need to make it executable and move it to the right place:

```

chmod a+x ./x.et
sudo cp ./x.et /usr/local/bin

```


5. Run "x.et" in a terminal, ET should run on a new X server. To access your desktop you need to press: 

```

CTRL + ALT + F7

```


6. To go back to ET by pressing:

```

CTRL +  ALT + F8

```


That's it! Another great benefit to this is that with the "x.et" script you don't even need to be running your desktop to play a game. Meaning if you boot up to "run level 3" or you quit gnome and gdm to get to a command prompt you can run "x.et" and it will still work saving even more resources!


Extra notes:

If like me you use an ~/.Xmodmap file to amend your mouse buttons (I have a Logitech mx510) then you need to add that like to the script aswell so that X server is configured properly like this example of my script:

```

#!/bin/bash
**xmodmap -display :1 -e "pointer = 1 2 3 6 7 8 9 10 4 5" &**
xinit /usr/local/games/enemy-territory/et $* -- :1

```

Obviously you need to put your own setting in the quotes but it's important you keep the ampersand (&) at the end to background the command or else your game will never run.

If you use the fabulous XQF then you can change the command to run "x.et" instead of just "et", that's a real winning combination! :)

Last but not least, it's a good idea to turn screensavers off so they don't load on your idle desktop while you're playing and suck up resources. It's probably a good idea to have the "Blank Screen Only" set which shouldn't affect performance.

Hope you like it :)

---

### Post by Nightblade on 2005-07-24
[QUOTE=endy]I already covered this in an unrelated post in the gaming forum and the nuts and bolts of this are all probably in the [linux-gamers.net](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=43) how to, but I like to keep things local here :)

Basically the ideas behind this is you run can run your games like Doom 3, Quake, Enemy Territory and pretty much anything in a new X server. The main benifit of this is that your dektop will get backgrounded which should give the game a performance boost and the ability to switch between your fullscreen game and your desktop, for example to check on an irc message.

I found this incredibly useful while clan gaming in the past as people would message me alot in irc while I played and otherwise I had to quit the game to see what it was. And now even though I don't play seriously any more I can't live without it. I will be using Enemy Territory as the example as it's my favorite game :)

"Enough already, show me the stuff" I hear you say, well ok then here you go:

1. First to allow you to run a new X display you need to edit the "/etc/X11/Xwrapper.config" file:

```

sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
sudo dpkg-reconfigure xserver-common

```Then  make sure you change the first option to "Anybody" and hit enter twice.


2. Create the script "x.et":

```

gedit x.et

```And paste the following:

```

#!/bin/bash
xinit /usr/local/games/enemy-territory/et $* -- :1

```


3. Now we need to make it executable and move it to the right place:

```

chmod a+x ./x.et
sudo cp ./x.et /usr/local/bin

```


4. Run "x.et" in a terminal, ET should run on a new X server. To access your desktop you need to press: 

```

CTRL + ALT + F7

```


5. To go back to ET by pressing:

```

CTRL +  ALT + F8

```


That's it! Another great benefit to this is that with the "x.et" script you don't even need to be running your desktop to play a game. Meaning if you boot up to "run level 3" or you quit gnome and gdm to get to a command prompt you can run "x.et" and it will still work saving even more resources!


Extra notes:

If like me you use an ~/.Xmodmap file to amend your mouse buttons (I have a Logitech mx510) then you need to add that like to the script aswell so that X server is configured properly like this example of my script:

```

#!/bin/bash
**xmodmap -display :1 -e "pointer = 1 2 3 6 7 8 9 10 4 5" &**
xinit /usr/local/games/enemy-territory/et $* -- :1

```

Obviously you need to put your own setting in the quotes but it's important you keep the ampersand (&) at the end to background the command or else your game will never run.

If you use the fabulous XQF then you can change the command to run "x.et" instead of just "et", that's a real winning combination! :)

Hope you like it :)[/QUOTE]
 I got "client rejected by server" or something when i ran this, just a checkerboard screen with a X in the middle. 

Also sudo md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum <- that line gave me permission denied on the part after >... =) Anyway, great guide, will be glad to use it when I make it work.

---

### Post by endy on 2005-07-24
Ok I did miss a whole part out.

*bangs head on desk *

Sorry about that, I've amended the how to and I hope it should work now. The bit about the xauth is kinda hard to explain, I've done my best but if you have any questions I'll do my best to clear it up. But if it all goes wrong on the xauth bit just type "quit" instead of "exit" and no changes will be saved.

Hope this does the trick this time :)

---

### Post by Nightblade on 2005-07-24
[QUOTE=endy]Ok I did miss a whole part out.

*bangs head on desk *

Sorry about that, I've amended the how to and I hope it should work now. The bit about the xauth is kinda hard to explain, I've done my best but if you have any questions I'll do my best to clear it up. But if it all goes wrong on the xauth bit just type "quit" instead of "exit" and no changes will be saved.

Hope this does the trick this time :)[/QUOTE]
 Yay! Works like a charm now :D Except for one thing... I usually run armyops with the aoss option before to have sound... is there a way to do that with xinit? Tried adding aoss before the path to armyops bin but no go...

Thanks for a great guide, been looking for this a long time.

---

### Post by shawn on 2005-07-24
This worked perfectly for my copy of Doom 3, I can now edit config files in gedit and switch back to Doom 3 and execute them. Incredibly slick!

Thank you very much endy - you just made gaming in Ubuntu a far more pleasant experience for me! :grin:  :grin:  :grin:

---

### Post by endy on 2005-07-25
[QUOTE=Nightblade]Yay! Works like a charm now :D Except for one thing... I usually run armyops with the aoss option before to have sound... is there a way to do that with xinit? Tried adding aoss before the path to armyops bin but no go...

Thanks for a great guide, been looking for this a long time.[/QUOTE]

If it's an argument for the game then you can pass it as you would usually, for example using enemy territory again, if I wanted to tell it to run in a window I'd type:

```

x.et +set r_fullscreen 0

```

Just like I would normall type:

```

et +set r_fullscreen 0

```

Does this help?

---

### Post by ishtvan222 on 2005-08-06
This is a great howto. I am having a problem tho. I can start it fine but then if i switch back to my desktop and then back to the game (CTRL ALT F6) all I see is the terminal output. I cannot acccess the game. It is still running because I can hear the music but I cannot get into the game.

Any ideas?

BTW im playing with Unreal Tournament 2004

edit: oops, never mind. I realized that the new X server is started on F8 and i thought it wud be on F6 because that is where i ran the command.

---

### Post by Jesus Franco on 2005-08-08
This seems very interesting.

I just wanted to know how would this increase performance? I would think running another X server would use up more ram. If thats not the case then awesome.  \\:D/

---

### Post by BanskuZ on 2005-08-09
Nice guide. I use this script:
```

#!/bin/bash
xinit $* -- :1 > /dev/null

```
And then: anotherscreen ~/your/path/to/game

---

### Post by muszek on 2005-08-11
Hi.  I did everything you mentioned exactly the same (the only difference is that I named the file x.armyops).  Got a unusual greyish background with an "x" mouse cursor and a (correct) armyops splash image.  Normally it's a black background.  Then (in the console) I saw it was terminated due to an error.  Here's the full output:

```
muszek@muszek:~$ x.armyops

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/muszek:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.war thogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux muszek 2.6.10-5-k7 #1 Fri Jun 24 18:51:20 UTC 20 05 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-k7 (buildd@vernadsky) (gcc version 3.3.5 (Debi an 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 18:51:20 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Aug 11 18:51:13 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No sym bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No sym bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No sy mbols found
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) fglrx(0): Failed to initialize UMM driver.
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

waiting for X server to shut down

```

Please help.

---

### Post by ridoo on 2005-08-12
Great work indeed endy :D

I can make everything you explain work but I have two problems.

1- I also use xmodmap but I'd like  to exec a file

xmodmap -display :1 -e "~/.etwolf/kbd_et" &
xinit /usr/local/games/enemy-territory/et $* -- :1 

it doesn't work 

2- Do we have to add the xauth line after every launch ?

thanks for help

---

### Post by endy on 2005-08-13
[QUOTE=Jesus Franco]This seems very interesting.

I just wanted to know how would this increase performance? I would think running another X server would use up more ram. If thats not the case then awesome.  \\:D/[/QUOTE]
AFAIK it backgrounds your original desktop, however I don't know enough about all this to say for sure this doesn't happen anyway but you can now jump between game and desktop pretty fast. On the other hand though, you can now easily run the game without running GDM and/or Gnome _at all_ which should of course give you the most benifit :)


[QUOTE=BanskuZ]Nice guide. I use this script:
```

#!/bin/bash
xinit $* -- :1 > /dev/null

```
And then: anotherscreen ~/your/path/to/game[/QUOTE]
Hey that's really neat too, I never thought of it like that - thanks! :)


[QUOTE=muszek]Hi.  I did everything you mentioned exactly the same (the only difference is that I named the file x.armyops).  Got a unusual greyish background with an "x" mouse cursor and a (correct) armyops splash image.  Normally it's a black background.  Then (in the console) I saw it was terminated due to an error.  Here's the full output:
<- snip ->

Please help.[/QUOTE]
From the look of your output all I can guess is that something is wrong with the OpenGL driver, is it an ATI card? If so I've never had one (I will do as soon the drivers get better) and I'd be out of my depth here... sorry :S


[QUOTE=ridoo]Great work indeed endy :D

I can make everything you explain work but I have two problems.

1- I also use xmodmap but I'd like  to exec a file

xmodmap -display :1 -e "~/.etwolf/kbd_et" &
xinit /usr/local/games/enemy-territory/et $* -- :1 

it doesn't work 

2- Do we have to add the xauth line after every launch ?

thanks for help[/QUOTE]
Ok I'll do my best to answer these in order :)

1. If you try this line in your script it should work:
```
xmodmap -display :1 ~/.etwolf/kbd_et &
```
2. No, once should be enough :)

---

### Post by ridoo on 2005-08-15
> Ok I'll do my best to answer these in order :)

1. If you try this line in your script it should work:
```
xmodmap -display :1 ~/.etwolf/kbd_et &
```


thanks, it works :D

> 2. No, once should be enough  

this not :(

i have to add the line each time i reboot
here is the code 
```

ridoo@simone:~$ sudo xauth
Password:
Using authority file /tmp/.gdmeFzU32
xauth> list
simone/unix:0  MIT-MAGIC-COOKIE-1  2f9eceb0dd4f3d259db5caa32cb6acb4
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  2f9eceb0dd4f3d259db5caa32cb6acb4
xauth> add :1.0 MIT-MAGIC-COOKIE-1 2f9eceb0dd4f3d259db5caa32cb6acb4
xauth> exit
Writing authority file /tmp/.gdmeFzU32
ridoo@simone:~$

```

---

### Post by awsome_petter on 2005-08-15
Could someone put an answer to the problem of muszek?, i have exaktly the same, and i am sick of exiting the game because someone send me an instan message, or i have to do something else:(

---

### Post by endy on 2005-08-15
[QUOTE=ridoo]
i have to add the line each time i reboot
here is the code 
```

ridoo@simone:~$ sudo xauth
Password:
Using authority file /tmp/.gdmeFzU32
xauth> list
simone/unix:0  MIT-MAGIC-COOKIE-1  2f9eceb0dd4f3d259db5caa32cb6acb4
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  2f9eceb0dd4f3d259db5caa32cb6acb4
xauth> add :1.0 MIT-MAGIC-COOKIE-1 2f9eceb0dd4f3d259db5caa32cb6acb4
xauth> exit
Writing authority file /tmp/.gdmeFzU32
ridoo@simone:~$

```[/QUOTE]
You don't need to be root so you can omit the "sudo" and do it as your normal user, hopefully that should do the trick :)

[QUOTE=awsome_petter]Could someone put an answer to the problem of muszek?, i have exaktly the same, and i am sick of exiting the game because someone send me an instan message, or i have to do something else:([/QUOTE]
Hi, you may be best trying to find a solution by starting a new topic, perhaps in the [Desktop Support](http://ubuntuforums.org/forumdisplay.php?f=65) forum and see if anyone can help you there, add as much info as possible. Sorry I can't help myself as I say I've no experience with ATI cards yet :(

---

### Post by muszek on 2005-08-15
[QUOTE=andy]From the look of your output all I can guess is that something is wrong with the OpenGL driver, is it an ATI card? If so I've never had one (I will do as soon the drivers get better) and I'd be out of my depth here... sorry :S[/QUOTE]
Yep, it's an ATI card, but seems to be configured well (I followed some guide on this forums, can't tell you which one, but glxgears shows ~1700 fps on a low end graphics card (radeon 9000 pro, I gave below $100 for it 3 years ago or so).

[QUOTE=awsome_petter]Could someone put an answer to the problem of muszek?, i have exaktly the same, and i am sick of exiting the game because someone send me an instan message, or i have to do something else:([/QUOTE]
My solution is to close everything that pops stuff (IM, RSS reader) before starting a game.  This doesn't annoy me a lot, but I kinda like like to read stuff (i.e. on ubuntufuroms :) ) while waiting for being respawned (fortunatelly I got good at not being killed).  Could this post be more off-topic?

---

### Post by awsome_petter on 2005-08-16
[QUOTE=muszek]Yep, it's an ATI card, but seems to be configured well (I followed some guide on this forums, can't tell you which one, but glxgears shows ~1700 fps on a low end graphics card (radeon 9000 pro, I gave below $100 for it 3 years ago or so).


My solution is to close everything that pops stuff (IM, RSS reader) before starting a game.  This doesn't annoy me a lot, but I kinda like like to read stuff (i.e. on ubuntufuroms :) ) while waiting for being respawned (fortunatelly I got good at not being killed).  Could this post be more off-topic?[/QUOTE]
 but somethimes it is necesary to have other program's that i must use while playing :D . When i'm trying to run ET on the other server it put's out that i have no hardware acceleration :( i had the same problem before i installed the Ati divers(and a lot of configuring and other things -_- ), it seems that he doesn't use the ati driver's. ??

---

### Post by endy on 2005-08-16
I'm not sure if this is related but it's an important note I forgot, you should turn screensavers OFF (you can set it to blank screen only) so while you're playing your game it doesn't load a screensaver on the idle desktop ;)

---

### Post by ridoo on 2005-08-16
[QUOTE=endy]You don't need to be root so you can omit the "sudo" and do it as your normal user, hopefully that should do the trick :) [/QUOTE]

I have already tried.
still doesn't work :(
It writes into a tmp file, is it what it has to do ?
After a reboot should I see the 3 lines ?


```
ridoo@simone:~$ xauth
Using authority file /tmp/.gdmsoIduu
xauth> list
simone/unix:0  MIT-MAGIC-COOKIE-1  a34527b0c7a2093a36656f755a13c8de
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  a34527b0c7a2093a36656f755a13c8de
xauth> exit

```

---

### Post by endy on 2005-08-18
Hmmm, that is strange, this is what happens for me:

```
endy@ananke:~$ xauth 
Using authority file **/home/endy/.Xauthority**

```

I'd be tempted to delete that "/tmp/.gdmsoIduu" file, log out and log back in. See if that makes any difference. However I'm not sure what could possibly go wrong from doing this but I've deleted mine in the past and I was OK  after loggin out and back in :)

EDIT: Also remove any ~/.Xauthority file as it appears that if that's corrupt GDM will make one in /tmp, hopefully this will work :)

---

### Post by ridoo on 2005-08-22
> EDIT: Also remove any ~/.Xauthority file as it appears that if that's corrupt GDM will make one in /tmp, hopefully this will work :)

great,

thanks for your help endy, everything is working fine now.

I made a french translation on [http://www.enemyterritory-fr.com/modules/ipboard/index.php?showtopic=2072&](http://www.enemyterritory-fr.com/modules/ipboard/index.php?showtopic=2072&).

---

### Post by Crube on 2005-08-24
I've got everything working fine, but it seems like my second xserver doesn't know how to use the right drivers. It seems to be using some kind of a defaul xorg.config file. I wonder why? It uses mesa drivers, and all the default settings (the ones I had the first after installin ) Might it be that the other server need a different config file? Afterall that would be nice for me, becouse I like running my games and desktop with different resolution.

EDIT: Is there a command for killing server #2?

---

### Post by endy on 2005-08-25
I just set the resolution options in the game and it sets the correct resolution on startup. It should be possible to run a new X server with a different xorg.conf file but I haven't found a way as yet with a few minutes testing so I can't help. If I do find out how I'll be sure to let you know :)

---

### Post by Crube on 2005-08-25
That would be nice, becouse the xserver starts with a pretty high resolution, and my game runs on smaller, and it sometimes causes random crashes during the resolution switch.

---

### Post by REBELinBLUE on 2005-08-27
This is really cool

Is there a way the script can be modifed to detect when the program finishes and so shuts down that x desktop?

---

### Post by Dr.Who on 2005-08-28
You should check out XGame:
[http://xgame.tlhiv.com/](http://xgame.tlhiv.com/)
which makes this much more uncomplicated. You create an extra xorg.conf for your games and this script which also comes in a GTK2 Gui version let you launch a new X session with that config. It let you define a DB of your games and acts as a launchpad,

Cheers,

Malte

---

### Post by nERDboY on 2005-08-28
[QUOTE=muszek]Hi.  I did everything you mentioned exactly the same (the only difference is that I named the file x.armyops).  Got a unusual greyish background with an "x" mouse cursor and a (correct) armyops splash image.  Normally it's a black background.  Then (in the console) I saw it was terminated due to an error.  Here's the full output:

```
muszek@muszek:~$ x.armyops

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/muszek:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.war thogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux muszek 2.6.10-5-k7 #1 Fri Jun 24 18:51:20 UTC 20 05 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-k7 (buildd@vernadsky) (gcc version 3.3.5 (Debi an 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 18:51:20 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Aug 11 18:51:13 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No sym bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No sym bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No sy mbols found
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) fglrx(0): Failed to initialize UMM driver.
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

waiting for X server to shut down

```

Please help.[/QUOTE]
 Does this thing work with counterstrike - source, 1.6 or condition zreo or all of them guess what im a fan of

---

### Post by ridoo on 2005-12-19
> Hmmm, that is strange, this is what happens for me:

Code:

endy@ananke:~$ xauth Using authority file /home/endy/.Xauthority


I'd be tempted to delete that "/tmp/.gdmsoIduu" file, log out and log back in. See if that makes any difference. However I'm not sure what could possibly go wrong from doing this but I've deleted mine in the past and I was OK after loggin out and back in

EDIT: Also remove any ~/.Xauthority file as it appears that if that's corrupt GDM will make one in /tmp, hopefully this will work 

Hi 

you already helped me about this .Xauthority problem.
When you told me to remove the ~/.Xauthority file and the /tmp/.gdmsoIduu I was under hoary.

Now I'm under breezy after a reinstall (not an upgrade).

I still have the same problem I had the first time (xauth write in the tmp/file )
I tried to delete both tmp and Xauthority, but now the Xauthority is not recreate and xauth still use the tmp file.

I really want to clear this problem.
Is there a way to recreate the Xauthority  file or to to force xauth to use it.

Thanks

---

### Post by ridoo on 2005-12-22
up :D 

I really want to solve this problem.
Nobody :(

---

### Post by pepolez on 2006-05-30
This guide worked fine for me except that i had to dpkg --reconfigure xserver-xorg rather then xfree86.

Enemy Territory runs fine except for one little bug - when i shut down the game and open it again and then join a game, the mouse just spins rapidly in a circle when I try to move it.

Tested on Ubuntu Dapper with xgl-gnome on primary desktop, artsd running, and et executable modified to start with artsdsp -m

---

### Post by pepolez on 2006-05-30
Since it was requested, here is my xorg config:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

## Devices
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

## Fonts
Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

## Modules
Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

## Maxtor 104 key US keyboard
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

## A4tech 'big thumb' optical mouse w/scrollwheel
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

## Wacom sapphire tablet
Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

## Wacom sapphire tablet - eraser
Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

## Wacom sapphire tablet - cursor
Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

## Auriga colorpro 17CF monitor
Section "Monitor"
    Identifier     "17 COLOR"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

## NVIDIA GeForce 6600GT AGP graphics card
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

## Auriga Colorpro 17CF monitor
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "17 COLOR"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by chadk on 2006-07-20
Can anyone update this for Dapper?  Seems the line:
md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
returns with an error about /etc/X11/Xwrapper.config not existing.

---

### Post by anaoum on 2006-07-21
> **chadk said:**
> Can anyone update this for Dapper?  Seems the line:
md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
returns with an error about /etc/X11/Xwrapper.config not existing.

happens for me too.

---

### Post by Poul on 2006-07-22
As above  + i get the following error trying to run the game. ```
pawel@pawel-p1500:~$ x.ao

X: user not authorized to run the X server, aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

---

### Post by punk84 on 2006-09-10
Just replace "xfree86" with "x11", after that it works. But for me inorder to run the script it has to be executed as root. I wish this was not the case.

punk84

---

### Post by Inferno. on 2006-10-20
Someone knows how can I use teamspeak with this? When I press the key to talk, nothing happend. But if i put the Ts on voice activation, everything works fine (But I don't want to use that). I tried to launch it in the same server than the game, but it's the same. There are no changes.

Sorry for the revive, I didn't want to make a new thread when I'm sure that someone here can help me to solve this.

Thanks in advance.

---

### Post by Bruegger on 2006-12-07
Hi Guys,
I had beryl-xgl installed with Dapper on my system.
I tried running stellarium and it wouldnt run.Learnt from some posts that i need to have another xserver to run it.But i dunno while the following endy's guide, i did something foolish and my xserver wont start. Using startx gets me into gnome...but  now i am not able to use beryl in it.
Is there a way i can undo the changes i made and get back to my old gnome with beryl-xgl???
Dont want to do a re-install of Dapper just for this.
Some one please help

P.S.I m a newbie with Linux and Dapper.

---

### Post by Bruegger on 2006-12-10
Some one please HELP!!!!
:confused:

---

### Post by rossjman1 on 2007-02-14
```
jeff@ubuntu:~$ sudo x.et

Fatal server error:
Server is already active for display 1
        If this server is no longer running, remove /tmp/.X1-lock
        and start again.

```
What do I do to fix this. I didn't understand the first step about changing the first option to Anybody. I don't know where or how to change this.

---

### Post by Jarn on 2007-03-25
When I do this, it works at first. But if I switch back to the other server (Ctrl+alt+F7) and then back to the one that a game is on, the game won't do anything. All I see is a black screen. I have the special cursor that the game has and can move it, but the screen is just black.

---

### Post by abrichr on 2007-07-26
It would be great to see this howto updated for Feisty.  I figured it out until: 

sudo dpkg-reconfigure xserver-common
Package `xserver-common' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-common is not installed

so i used dpkg-reconfigure xserver-xorg, which led me through a bunch of steps, but didn't ask me to specify anything about an option for "Anybody"

---

### Post by redsox59 on 2007-08-04
I'm in the same boat for the fiesty update

---

### Post by tonyisntcreative on 2007-09-08
And I'll make three.

EDIT: Nevermind, I figured it out, and it was quite simple, too.  Instead of xserver-common just replace it with x11-common.  Voila!

---

### Post by dakoth on 2007-10-05
Managed to get this working great, with one exception; I'm not sure how to change the display on the "second X" to a certain resolution/refreshrate prior to launching the game. Anyone mind giving me a hand?

edit: Never mind, I managed to solve it by changing the resolution/refreshrate the game starts in.

edit2: It did spawn a second problem though. When I swap back to the game I'm stuck in what appears to be the boot-terminal (can see all these lines going: * Checking something... [OK]). I can tell the game is still running as it plays sounds and all in the background, but I can't seem to get it back "on top".

edit3: Heh, never mind. Stupid of me to assume that my secondary X window would land on the same number. It popped up on ctrl-alt-f9 instead.

---

### Post by Ryback on 2007-12-29
> **tonyisntcreative said:**
> And I'll make three.

EDIT: Nevermind, I figured it out, and it was quite simple, too.  Instead of xserver-common just replace it with x11-common.  Voila!

Thanks, that helped me out.  I figured out the x11 filepath for the Xwrapper.config.md5sum work, but didn't apply the same logic to the x11-common!  I made an updated version of this How To at the enemyterritory forums [linked here]("http://community.enemyterritory.com/forums/showthread.php?p=257699").  Kudos to Endy :)

---

### Post by giannimesa on 2008-01-29
great!!! It works!!! great how to...

But I have a problem... :( sound doesn't work...  I try to copy and paste my current ET luncher... :

./et-sdl-sound

(with this luncher sound work in the first X server)

how can I do??

Thanks...

---

### Post by giannimesa on 2008-01-30
I resolve it,

I only copy the two scripts ( one to lunch ET in other X server, and one to lunch ET with sound) in mai dyrectory of ET and correct the rispective path in the lunchers... 

great... ;)

---

### Post by Kekk0 on 2008-06-03
> **endy said:**
> I already covered this in an unrelated post in the gaming forum and the nuts and bolts of this are all probably in the [linux-gamers.net](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=43) how to, but I like to keep things local here :)

Basically the ideas behind this is you run can run your games like Doom 3, Quake, Enemy Territory and pretty much anything in a new X server. The main benifit of this is that your dektop will get backgrounded which should give the game a performance boost and the ability to switch between your fullscreen game and your desktop, for example to check on an irc message.

I found this incredibly useful while clan gaming in the past as people would message me alot in irc while I played and otherwise I had to quit the game to see what it was. And now even though I don't play seriously any more I can't live without it. I will be using Enemy Territory as the example as it's my favorite game :)

"Enough already, show me the stuff" I hear you say, well ok then here you go:


1. First to allow you to run a new X display you need to edit the "/etc/X11/Xwrapper.config" file:

```

sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo su
md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
exit
sudo dpkg-reconfigure xserver-common


```Then  make sure you change the first option to "Anybody" and hit enter twice.


2. Next we have to set your ~/.Xauthority file up. This may look tricky but it's very straight forward, all you need to do is add a line using a special key we find. So, in a terminal type:

```

xauth
list

```And you should get an output something like this:

```

ananke/unix:0  MIT-MAGIC-COOKIE-1  **9fde426e5g03b20f4b7e51cb329d3033**
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  **9fde426e5g03b20f4b7e51cb329d3033**

```Yours WILL be different, thats ok. Now we need to add a new line and then exit to save it. So we type in "add :1.0 MIT-MAGIC-COOKIE-1" followed by that long alpha numeric string. I've highlighted mine in bold above so you know what I'm talking about but remember to use yours. So for me I would type the following:

```

add :1.0 MIT-MAGIC-COOKIE-1 9fde426e5g03b20f4b7e51cb329d3033
exit

```Remember YOU have to use YOUR OWN sting of numbers and letters copied form the output we got earlier, mine is just an example. Ok? I know it's a bit abstract but hopefully this is clear enough.


3. Create the script "x.et":

```

gedit x.et

```And paste the following:

```

#!/bin/bash
xinit /usr/local/games/enemy-territory/et $* -- :1

```


4. Now we need to make it executable and move it to the right place:

```

chmod a+x ./x.et
sudo cp ./x.et /usr/local/bin

```


5. Run "x.et" in a terminal, ET should run on a new X server. To access your desktop you need to press: 

```

CTRL + ALT + F7

```


6. To go back to ET by pressing:

```

CTRL +  ALT + F8

```


That's it! Another great benefit to this is that with the "x.et" script you don't even need to be running your desktop to play a game. Meaning if you boot up to "run level 3" or you quit gnome and gdm to get to a command prompt you can run "x.et" and it will still work saving even more resources!


Extra notes:

If like me you use an ~/.Xmodmap file to amend your mouse buttons (I have a Logitech mx510) then you need to add that like to the script aswell so that X server is configured properly like this example of my script:

```

#!/bin/bash
**xmodmap -display :1 -e "pointer = 1 2 3 6 7 8 9 10 4 5" &**
xinit /usr/local/games/enemy-territory/et $* -- :1

```

Obviously you need to put your own setting in the quotes but it's important you keep the ampersand (&) at the end to background the command or else your game will never run.

If you use the fabulous XQF then you can change the command to run "x.et" instead of just "et", that's a real winning combination! :)

Last but not least, it's a good idea to turn screensavers off so they don't load on your idle desktop while you're playing and suck up resources. It's probably a good idea to have the "Blank Screen Only" set which shouldn't affect performance.

Hope you like it :)


Can't get it to work..
It says like "xserver is not installed" or something like that :S

---

### Post by biriachan on 2008-06-05
I had the same problem at first, Currently running Hardy Heron 64bit.

There are a few changes I made to step 1 based on various post made in this thread by others.

Step 1:
- Orginal
```
sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo su
md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
exit
sudo dpkg-reconfigure xserver-common
```
- Modified
```
sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo su
md5sum /etc/X11/Xwrapper.config > /var/lib/x11/Xwrapper.config.md5sum
exit
sudo dpkg-reconfigure x11-common
```

As a test I used the game BTanks

x.et ->
```
#!/bin/bash
xinit /usr/games/btanks $* -- :1
```

I also recommend looking at this thread 
[http://ubuntuforums.org/showthread.php?t=552805]("http://ubuntuforums.org/showthread.php?t=552805")



Currently I an running dual monitors. My xorg.conf file was generated using nvidia-settings (TwinView) with a few modifications made by hand.

Right now my 2nd Xserver is using my current xorg.conf (Dual Monitors).  My main reason for using a 2nd Xserver is to use only my main monitor as have I had big problems with game centering themselves between both monitors.

Is there a way I can load a different xorg.conf configuration or make some modification to my current xorg.conf to use only one monitor in my 2nd Xserver?


Never mind - Found I could edit my xorg.conf.
Change the meta modes 
"metamodes" "CRT-0: 1600x1200_85 +1280+0, CRT-1: 1280x1024_60 +0+0;
-Changed all others 
CRT-0: 1024x768_85, CRT1: NULL;

NULL disables my 2nd monitor

---

### Post by Hetor on 2009-06-10
```
HetorsLAB hetor # md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
bash: /var/lib/xfree86/Xwrapper.config.md5sum: No such file or directory
```

I have /var/lib/x11/Xwrapper.config.md5sum though, will it work?

---

### Post by Gen2ly on 2009-07-28
> **Hetor said:**
> ```
HetorsLAB hetor # md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
bash: /var/lib/xfree86/Xwrapper.config.md5sum: No such file or directory
```

I have /var/lib/x11/Xwrapper.config.md5sum though, will it work?

For xorg 1.6 a few things have changed.  You can change displays and enable keyboard/mouse with this script:

```
#!/bin/bash

DISPLAY=:1.0

xinit $* -- :1
```

This will also open a terminal window where you can launch your game from.

---

### Post by Cebonet on 2009-10-03
Yes! I  got it working with doom3, but when I switch from the game to the desktop and back, the whole thing turns to a command prompt. 

How do I create a new x server with counter-strike source(steam) on wine?:confused:

---

### Post by mnml on 2010-01-01
I tried this but I get an error when I try to run xterm or any app for example with this cmd:
xinit xterm $* -- :1
I get:

```
Backtrace:
0: X(xorg_backtrace+0x26) [0x4f00c6]
1: X(xf86SigHandler+0x41) [0x4852c1]
2: /lib/libc.so.6 [0x7feb3caf5530]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(Phw770_ProgramMemoryTimingParameters+0x81) [0x7feb3b152f21]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7feb3b1572a8]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0xf0) [0x7feb3b124df0]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x3b) [0x7feb3b1234bb]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7feb3b166a88]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x248) [0x7feb3b165fb8]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x1f) [0x7feb3b14762f]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x64) [0x7feb3b145ee4]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x23) [0x7feb3b144583]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x25) [0x7feb3b144635]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x187) [0x7feb3b1448c7]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7feb3b121c62]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x28) [0x7feb3b121848]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0x90) [0x7feb3b0e93d0]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x3f) [0x7feb3b0ac72f]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7feb3b0ef345]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7feb3b0ed6ef]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0xbb) [0x7feb3b0ed85b]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0x9a) [0x7feb3b0ee35a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x35d) [0x7feb3b0ec74d]
23: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0xe52) [0x7feb3b0ad5b2]
24: X(InitOutput+0x507) [0x46f017]
25: X(main+0x1fe) [0x433ece]
26: /lib/libc.so.6(__libc_start_main+0xfd) [0x7feb3cae0abd]
27: X [0x433509]
Saw signal 8.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

edit: I just found a bug report about it, still looking for a solution.

[https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/489800](https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/489800)

---

### Post by Mirror Shades on 2010-06-11
Hey guys,

I'm pretty new to Ubuntu as a whole (5 days of experience lol, but I'm trying to get it) and I've configured my x.et according to this guide, but when I try to run it in terminal it just starts and shuts down immediately, outputting this last line:

> xinit:  No such file or directory (errno 2):  no program named "/media/MEDIA/Games/WoW 3.3.3a/WoW.exe" in PATH


I'll explain things a bit further: I'm trying to run World of Warcraft through x.et file, which I filled like that:

> #!/bin/bash
xinit /media/MEDIA/Games/"WoW 3.3.3a"/WoW.exe $* -- :1

I suppose this is wrong, because it should run through wine and I haven't pointed that out to the X server (because I don't know how), at least I think so. Could you guys lend me a hand in making this to run? Thanks in advance :)

BTW I'm using Ubuntu 10.04 if that is of any help.

---

### Post by Cristiano MM on 2010-10-26
I managed to get wow to work by using this tutorial thanks alot:D

huge fps jump.

---

### Post by Baddreamz on 2011-07-24
xinit /usr/bin/wine game.exe -- :1


i used this following comand to start a new server.


but one thing i caný understand is why do i have less fps on the new x server
than running the game normally?oO
regards

---

### Post by mbiela on 2012-06-23
Hi,

i can`t manage with start game on new X server using wolfsp-sdl-sound script. 

giannimesa wrote:

> I resolve it,

I only copy the two scripts ( one to lunch ET in other X server, and one  to lunch ET with sound) in mai dyrectory of ET and correct the  rispective path in the lunchers...

but he did not wrote what exactly he did (which path). For now, I can only start game on new X server, but sound stays on first :(
Can anyone help me to solve this problem?

Sorry for poor english.

mbiela

---

### Post by Alchemek on 2012-08-06
I've followed all the directions and it appears to work, but what's ridiculous is that once I switch over to my desktop, I can't switch back without my game being gone. Makes no sense.

(==) Log file: "/var/log/Xorg.1.log", Time: Mon Aug  6 15:40:49 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
Home directory /home/alchemek not ours.
warning: The VAD has been replaced by a hack pending a complete rewrite
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000023, ulEventData = 00000001

---

