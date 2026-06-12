---
title: "WOW in Wine keyboard problems"
date: 2009-04-08
forum: Wine
---

### Post by callie510 on 2009-04-08
I have searched and searched and searched... I apologize if this is a problem that has been solved, but I certainly can't find a solution. Although I'm kinda a newbie at this stuff... WOW appears to run in Wine perfectly well for most people, so I'm hoping this is a config problem.

I have a perfectly good Windows XP installation on another partition, so I start wow with "wine "/media/disk/Program Files/World of Warcraft/Wow.exe" -opengl" ... The login screen appears to load just fine, but I only get 1 or 2 keyboard presses in before I lose the keyboard entirely. I can do anything I want with the mouse, but no keyboard input works.

I haven't found anyone else with this problem so I'm hoping it's just a Wine configuration setting I don't have right.

1) Wine version: don't really know how to check this, but synaptic says I have Wine v 1.0.1ubuntu2 installed.

2) Yes, I am running it in a Wine desktop, and I have tried clicking the desktop window to focus it. Still no dice.

Please help...?

edit: oops, I posted this in the wrong forum entirely... sorry... :|

---

### Post by rafemonkey on 2009-04-22
I'm having the same problem. Not with WOW, but with other games. (homeworld and starcraft) I have a theory that this may be because of my keyboard/mouse set up... in particular I think wine doesn't like it when the keyboard and mouse share a port. What kind of setup do you have?

---

### Post by Neverwin on 2009-05-05
I have this problem too. Sort of. I can use the keyboard in wow until i tab out and back. Then only the mouse works. It doesn't recognize holding down a button either i just get pulses until another button is pressed at the same time. If your wow-window looses focus for some reason (like a hardware volume control or some message from another process) disabling that might be a temporary sollution... Otherwise it worked much better with ubuntu 8.10 if you wanna go that far to play.

---

### Post by dabang on 2009-05-05
Not sure, could it be related to this?
[http://ubuntuforums.org/showthread.php?t=1119615&highlight=wow](http://ubuntuforums.org/showthread.php?t=1119615&highlight=wow)

And maybe try updating to latest Wine from [http://www.winehq.org/](http://www.winehq.org/) (They provide a howto)

---

### Post by MonkeyPlus on 2009-05-06
Are you trying to get wine to run your Windows install of World of Warcraft? You should try installing it no your Linux partition, by running the installer programme under Wine. There are plenty of instructions around the forums on how to do that.

---

### Post by dabang on 2009-05-06
> You should try installing it no your Linux partition...

Not really necessary, but you may think about copying your WoW program directory from Windows to ~/.wine/drive_c/Program Files. I have no issues running WoW within wine (latest version from winehq).

---

