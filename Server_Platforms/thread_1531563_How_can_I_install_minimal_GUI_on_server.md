---
title: "How can I install minimal GUI on server"
date: 2010-07-15
forum: Server Platforms
---

### Post by The Cog on 2010-07-15
I just installed Ubuntu 10.04 server, no problems.

Some of my windows-oriented workmates insist it's got to have a GUI so they can use nautilus and gedit. I've seen a number of suggestions to install ubuntu-desktop, but that drags in a load of stuff I don't want - I don't want a print server and all those other desktop support services. Just a basic window manager, file manager and editor that can run under startx when needed.

I thought maybe installing gnome might do the trick, but it won't install:
> ~$ sudo apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages


I'm not sure that gnome is the right package anyway. Please can someone point me in the right direction?

P.S.
Installing nautilus, gedit and xinit got me partway there, but I didn't get the window manager which made using the windows difficult.

---

### Post by sisco311 on 2010-07-15
gnome-core depends on a basic set of programs, including a file manager, an image viewer, a text editor and other basic tools.

But, check out the community documentation for alternatives:

[https://help.ubuntu.com/community/Installation/LowMemorySystems#Preparing%20for%20Graphical%20Environment](https://help.ubuntu.com/community/Installation/LowMemorySystems#Preparing%20for%20Graphical%20Environment)

HTH

---

### Post by The Cog on 2010-07-15
gnome-core was just the ticket, thank you. 
I also had to install xinit for startx to work, but otherwise, perfect. 

The other lightweight desktops would probably have done except for issues with familiarity.

---

### Post by gr4nf on 2010-07-15
If all you really need is a text editor and a file manager, you should just teach your workmates the very few basic file navigation commands and show them the nano text editor. You'll save a lot of space and extra time, not to mention that nano is as intuitive and easy as gedit ever was.

If they absolutely don't get it, I would still recommend gnome, as it is reliable and powerful, but don't install it with ubuntu-desktop, as it is true that that comes with a bunch of extra stuff. Get the packages manually:
```

sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

```

---

### Post by The Cog on 2010-07-15
Hah! I'm working on them, but it's slow going.

---

