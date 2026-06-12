---
title: "If I install the meta package 'gnome' will it destroy my current unity install?"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by georgelappies on 2012-04-14
In synaptic there is a meta package called 'gnome'. If you select that it wants to install all the gnome stuff including gdm. If I want to try out gnome shell should I install this? Or will this bork up my unity install to a FUBAR state?

---

### Post by wojox on 2012-04-14
No it won't bork it up. If you want gnome-shell search for that. If you install gnome-tweak-tool it will install gnome-shell.

I installed this through the terminal and got the ncurses screen about keeping lightdm or configuring gdm. :p

---

### Post by keithpeter on 2012-04-14
Hello All

The gnome package brings Evolution, Epithany Web browser and other stuff with it. When gdm is being installed, you'll get an ncurses style box pop up and ask you which desktop manager you want, gdm or lightdm. 

As wojox said, if all you want is to try Gnome Shell, just install gnome-shell

I personally tried a mini iso install of a command line system and just apt-get install gnome-core, which gave me a basic desktop without any applications.

Mind you, I've gone back to Unity on the present test install...

---

