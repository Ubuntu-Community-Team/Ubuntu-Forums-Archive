---
title: "server + ubuntu or xubuntu - difference?"
date: 2006-08-01
forum: Server Platforms
---

### Post by printmkr on 2006-08-01
I understand I can install the Ubuntu Server, and afterwards and a window manager if I need my warm and fuzzy GUI (coming from Windows and Mac here.) This will not be a high traffic server... it will be running Apache 2.2, MySQL 5, PHP 5, Ruby and Mongrel.

Would there be a noticable difference if instead of installing Ubuntu I installed Xubuntu (which I understand takes less resources)? Or is there not much difference between the two in this situation-- as opposed to having no Windows Manager at all?

I just don't feel comfortable doing it all from the command line yet... thanks for any input!

---

### Post by kripkenstein on 2006-08-01
Just throwing out numbers - meaningless numbers, mostly - say that Xfce (Xubuntu) adds 50 megs over just a console, and GNOME (normal Ubuntu desktop) adds another 50, for a total of 100 megs over a console. That's about the right area, I'd say.

Whether 50-100 megs of RAM is meaningful to you, depends on the machine, how much load it is under, and so forth. Of course, you can install and later remove a desktop environment, or install both and choose at boot time which to use (or even the console). Ubuntu is very convenient with this stuff.

If you only need some minimal GUI usage, then perhaps try Xfce. My personal recommendation would be to try to do more things from the console, though - in the long term, that is the way to go :)

---

### Post by houstonbofh on 2006-08-01
> **printmkr said:**
> I understand I can install the Ubuntu Server, and afterwards and a window manager if I need my warm and fuzzy GUI (coming from Windows and Mac here.) This will not be a high traffic server... it will be running Apache 2.2, MySQL 5, PHP 5, Ruby and Mongrel.

Would there be a noticable difference if instead of installing Ubuntu I installed Xubuntu (which I understand takes less resources)? Or is there not much difference between the two in this situation-- as opposed to having no Windows Manager at all?

I just don't feel comfortable doing it all from the command line yet... thanks for any input!

Ubuntu uses Gnome.  It is quite mature, and very pretty.  It is also a little fat.  XUbuntu uses Xfe.  It is lightweight, but less pretty.  It also has some less mature tools for basic system administration.  It also does not load Open Office by default...  Either way, you will save some weight cleaning out the parts you do not need.  As to which is better, I am still deciding.  I am going to make 2 identical systems (P2 866 256mb) and let the office girl use them for a while.  Then see which one she uses most.

---

### Post by Akita on 2006-08-02
Xubuntu is lighter but still throws a bunch of (primarily) desktop apps on the box that you probably don't want on a server. 

Try something like:

apt-get install xfce4 xubuntu-system-tools xubuntu-default-settings mousepad thunar

That'll get you xfce4 (xubuntus window manager) and the xubuntu look & feel with base appletts. Mousepad is the xubuntu text editor and Thunar is the file manager.

That's pretty minimal and 1/2 the size of an XUbuntu install.

Oh, add gdm to the list if you want the server to come up in GUI mode... otherwise do "startx" at a command prompt.

---

### Post by printmkr on 2006-08-03
This sounds like a great compromise! It is funny that you mention a GUI text editor... editing config files, etc from the command line is one of my big phobias! thanks for the detailed help and I'll give it a shot.

---

