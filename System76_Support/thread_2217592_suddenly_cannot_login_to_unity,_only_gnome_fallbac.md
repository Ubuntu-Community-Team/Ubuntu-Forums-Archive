---
title: "suddenly cannot login to unity, only gnome fallback"
date: 2014-04-18
forum: System76 Support
---

### Post by system76panp9 on 2014-04-18
I am running Ubuntu 13.04 on a System 76 panp 9 laptop.
Suddenly one day when I tried to login as normal, I got a
blank desktop with only the wallpaper showing, no unity
panels or anything. When I switched to Gnome Fallback
login option, I could login and get the gnome desktop ok,
and then if I went into Compiz Configuration manager, I
could check the Unity plugin and the unity launcher etc
would show up again, but still not at the next login. I am
actually happier with Gnome Fallback but I want to debug
what went wrong with Unity especially since I have also
now been having some instability relating to the window
manager, for instance, metacity window decoration themes
are not respected and occasionally the window manager
suddenly crashes and leaves windows undecorated. I
think these problems may be related. I would appreciate
any help with some diagnostics I might try to examine
to discover why these bugs are suddenly occurring after
I have been using my system for nearly a year and
did not make any significant changes that I can think of
immediately before the new behavior started showing up.
Thanks in advance for any information ...

---

### Post by christopherbalz on 2014-04-19
Same issue, upgrading from 12.04 LTS to 14.04 LTS.  Only saw the Unity desktop the first time I logged in, but its gear icon and other deskbar widgets were obscured.  Followed the instructions for installing the system76 driver for my nvidia card, restarted and updated, but that did not fix.

---

### Post by christopherbalz on 2014-04-19
This got the Unity desktop back, but it was still missing the top-right icons (gear icon, etc): [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)    

Still, much more familiar.  Must shutdown though via command line since I don't have the gui for that yet.

---

### Post by christopherbalz on 2014-04-19
Fixed for me: dconf reset -f /org/compiz/ && unity --reset-icons &disown[COLOR=#444444][FONT=UbuntuRegular]  per this thread: [/FONT][/COLOR]http://askubuntu.com/questions/286088/menu-bar-and-launcher-missing-in-ubuntu-13-04

---

### Post by raphievila on 2014-04-23
I don't get anything in my desktop, when Ctrl+Alt+F2, login and try to run dconf says I need X11 DISPLAY. set the variable as DISPLAY=:0.0 and still says can't read DISPLAY:0.0, and I can't access anything throught the desktop, not even Ctrl+Alt-T for the terminal, nothing show up, only wallpaper.

- I follow suggetion @ [http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels/204438#204438](http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels/204438#204438), unistall desktop not by suggested answered but by hafichuck. Also, uninstall the nvidia driver, then reboot. Apparently everything is working now. Now need to see what else did is broken.

I have a i7 Intel CPU, with an Nvidia GeForce 550 ti... hope it help anyone else who's dconf reset -f /org/compiz/ not working.

---

