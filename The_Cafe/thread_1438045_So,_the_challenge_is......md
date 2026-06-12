---
title: "So, the challenge is....."
date: 2010-03-24
forum: The Cafe
---

### Post by dragos240 on 2010-03-24
To get a linux system up with X (Xorg or Xvesa), and have a window manager. The only catch is to have it accumulate less than 32mb of ram. How would I go about doing this?

---

### Post by Regenweald on 2010-03-24
Install [Slitaz ?](http://www.slitaz.org/en/)

---

### Post by NightwishFan on 2010-03-24
DSL?
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by dragos240 on 2010-03-24
......From an existing distro............

---

### Post by blueturtl on 2010-03-24
Which distro?

In Debian/Ubuntu I would just purge all gnome related packages, possibly even GDM and then do a

sudo apt-get install xinit fluxbox

You have to be a bit more spesific though, I don't want you to ruin your system following my advice. :)

---

### Post by dragos240 on 2010-03-24
Gentoo.

---

### Post by Pogeymanz on 2010-03-24
Xorg comes with a window manager called TWM. If that is above 32MB, you're out.

---

### Post by Psumi on 2010-03-24
> **Pogeymanz said:**
> Xorg comes with a window manager called TWM. If that is above 32MB, you're out.

I love how TWM makes the xfce4 panel a window that I can't use.

---

### Post by new_tolinux on 2010-03-24
Don't know what you mean with "Window manager", but I think I have some RedHat 5.1 around somewhere....

;)

---

### Post by Psumi on 2010-03-24
> **new_tolinux said:**
> Don't know what you mean with "Window manager", but I think I have some RedHat 5.1 around somewhere....

;)

OpenBox? TWM? XFWM4? Metacity?

windows has Window Managers too.

---

### Post by K.Mandla on 2010-03-24
Been there, done that.

[http://kmandla.wordpress.com/2009/02/15/how-can-it-all-fit/](http://kmandla.wordpress.com/2009/02/15/how-can-it-all-fit/)
[http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/](http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/)

---

### Post by Shpongle on 2010-03-24
just done it , debian lenny net install , install the base system , xorg , openbox , iceweasel (optional) so far its at 28 mb

---

### Post by Psumi on 2010-03-24
> **DillByrne said:**
> just done it , debian lenny net install , install the base system , xorg , openbox , iceweasel (optional) so far its at 28 mb

Adding tint2 to that would make it how much?

---

### Post by Shpongle on 2010-03-24
> **Psumi said:**
> Adding tint2 to that would make it how much?

I havnt got around to it yet , because i'm busy with assignments and all but i doubt it would be too much , i'm doing it all in virtual box . Il post back during the week when i have time to mess with it.

---

### Post by Psumi on 2010-03-24
> **DillByrne said:**
> I havnt got around to it yet , because i'm busy with assignments and all but i doubt it would be too much , i'm doing it all in virtual box . Il post back during the week when i have time to mess with it.

In ubuntu, tint2 took about 5-15 MB of RAM :|

---

### Post by Yes on 2010-03-24
BasicLinux can do that in 8 MB of RAM.

---

