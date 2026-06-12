---
title: "I managed to install the nvidia driver on Ubuntu Server!"
date: 2009-06-13
forum: The Cafe
---

### Post by ninja_numbnuts on 2009-06-13
I'm not showing off, I'm just proud of myself! :D

---

### Post by ad_267 on 2009-06-13
sudo apt-get install nvidia-glx-180?

---

### Post by Daisuke_Aramaki on 2009-06-13
A serious thread merge is on the horizon! :p

---

### Post by ninja_numbnuts on 2009-06-13
Lol, no I didn't try that, I was trying to install thelatest 185.18.14 from nvidias site, but there was a problem with it recognizing the kernel source tree.

---

### Post by ninja_numbnuts on 2009-06-13
> **Daisuke_Aramaki said:**
> A serious thread merge is on the horizon! :p

:p

---

### Post by v8YKxgHe on 2009-06-13
Since when do servers require graphics drivers? Well, no require - maybe a better question: Why? :P

---

### Post by Sealbhach on 2009-06-13
> **AlexC_ said:**
> Since when do servers require graphics drivers? Well, no require - maybe a better question: Why? :P

I was wondering that too.

But congrats to OP, well done. =D>

.

---

### Post by Delever on 2009-06-13
You could just do "apt-get install ubuntu-desktop" and have full ubuntu. Did you know that?

---

### Post by Firestem4 on 2009-06-13
> **AlexC_ said:**
> Since when do servers require graphics drivers? Well, no require - maybe a better question: Why? :P

why not? a server doesn't HAVE to be all command-line...Sometimes tools are better performed through a gui than a command line. 

(yes, all you command-line zealots, its true! lol)

---

### Post by Deamos on 2009-06-13
> **Firestem4 said:**
> why not? a server doesn't HAVE to be all command-line...Sometimes tools are better performed through a gui than a command line. 

(yes, all you command-line zealots, its true! lol)

Point of running Server vs Desktop version is the fact that the kernel is made for server based processes and runs better w/o a GUI.  

GUIs on a server steal the resources needed for things like apache and other server processes.   

If you need some type of GUI for a server install, use web based administration tools like Webmin :)

---

### Post by ninja_numbnuts on 2009-06-13
> **AlexC_ said:**
> Since when do servers require graphics drivers? Well, no require - maybe a better question: Why? :P

I am using a desktop. I wanted something that I could build to my liking without having to use Gnome, KDE or XFCE. I'm using Fluxbox, and the speed is really quick! Firefox launches nearly straight away!

> **Sealbhach said:**
> I was wondering that too.

But congrats to OP, well done. =D>
.

Thank you! :D


> **Delever said:**
> You could just do "apt-get install ubuntu-desktop" and have full ubuntu. Did you know that?

No I didn't. But I don't want Gnome and all the things that come with it, I wanted to build the system my way. I'm not good enough with the command line to install Arch yet!

---

### Post by Mehall on 2009-06-13
> **ninja_numbnuts said:**
> I am using a desktop. I wanted something that I could build to my liking without having to use Gnome, KDE or XFCE. I'm using Fluxbox, and the speed is really quick! Firefox launches nearly straight away!



Thank you! :D




No I didn't. But I don't want Gnome and all the things that come with it, I wanted to build the system my way. I'm not good enough with the command line to install Arch yet!



Doing it from server isn't the way you should go about that.

If you get the alternate install disc, when it boots, you can press F4 on the boot menu to change mode. Change to "CLI install" mode, and it installs a system for the desktop (inc. desktop kernel) but without the DE.

EDIT: you can also do it from the mini.iso

---

