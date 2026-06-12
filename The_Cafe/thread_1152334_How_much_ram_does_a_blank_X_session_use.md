---
title: "How much ram does a blank X session use?"
date: 2009-05-07
forum: The Cafe
---

### Post by dragos240 on 2009-05-07
Just one that doesn't have anything, no GUI, no window manager, no desktop environment, not even a terminal emulator, just completely blank.

---

### Post by kk0sse54 on 2009-05-07
Very, very little, try it out yourself. I think last time I did it was around 12 MB although K. Mandla succeeded with a window manager to get 12 MB I think.

---

### Post by dragos240 on 2009-05-07
What would it be with fluxbox? Anyways, how can you have a blank one anyways? When I startx it displays my gnome setup. :\

---

### Post by kk0sse54 on 2009-05-07
> **dragos240 said:**
> What would it be with fluxbox? Anyways, how can you have a blank one anyways? When I startx it displays my gnome setup. :\

If you use GDM disable the daemon and then make sure your ~/.xinitrc is blank when typing startx

---

### Post by damis648 on 2009-05-07
As in enter a terminal (Ctrl+Alt+F1) and type in:
```
sudo /etc/init.d/gdm stop
mv ~/.xinitrc .xinitrc.bak
X # or startx
```
and then when you are done:
m```
v ~/.xinitrc.bak ~/.xinitrc
```

---

### Post by Daisuke_Aramaki on 2009-05-07
i ran 19mb with evilwm on an old machine. it was a very minimal crux/lunar setup.

fluxbox is very easy on resources as well. but the memory footprint depends on so many other things, like how many daemons and supporting processes are running. 

on a no X setup, which i still use quite often i hit 37-50 mb mostly, with framebuffer, dvtm running a few instances of vim, elinks, and mpd to give you an idea.

---

### Post by dragos240 on 2009-05-07
Ahh crud.

My home folder doesn't contain a .xinitrc, but it does contain a .bashrc. Is this for root?

---

### Post by kerry_s on 2009-05-07
my laptops 21mb on boot with jwm on arch linux, no login manager, uses inittab to autologin and .bash_profile to auto startx.

---

### Post by RiceMonster on 2009-05-07
> **dragos240 said:**
> Ahh crud.

My home folder doesn't contain a .xinitrc, but it does contain a .bashrc. Is this for root?

you can still run X without a .xinitrc. That file just tells X what to run when you start X. So if you don't have one, you'll launch a blank X session. You can create a .xinitrc yourself, as well. Also, .bashrc is your bash config file.

---

### Post by dragos240 on 2009-05-07
thanks :)

---

