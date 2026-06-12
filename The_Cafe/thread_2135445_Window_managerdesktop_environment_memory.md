---
title: "Window manager/desktop environment memory"
date: 2013-04-14
forum: The Cafe
---

### Post by screamingjazz on 2013-04-14
I've found this interesting article regarding the amount of memory used by a number of window managers and desktop environments.

[http://l3net.wordpress.com/2013/04/09/a-memory-comparison-of-light-linux-desktops-part-2/](http://l3net.wordpress.com/2013/04/09/a-memory-comparison-of-light-linux-desktops-part-2/)

Beyond the regular unity, gnome, kde, lxde and xfce, is anybody using anything else in Ubuntu? Am I alone running Fluxbox?

---

### Post by mips on 2013-04-14
That comparison is flawed as he seems to have tested all those DE/WM's on top of Ubuntu which in itself adds a lot of stuff not required. Such a test should ideally be done on a netinstall in a VM where you snapshot the base install and then measure each environment.

My laptop runs openbox and my desktop xfce.

---

### Post by ibjsb4 on 2013-04-14
Nice reference.  With the way Nautilus is going, make me wonder if its worth it.

---

### Post by mag1strate on 2013-04-14
I feel that the memory usage really shouldn't be a problem...I mean 192MB is not much when compared to the 4-16GB most new computers have pre-installed.

This is great for looking at ideas for old computers though!

---

### Post by ibjsb4 on 2013-04-14
> **mips said:**
> That comparison is flawed as he seems to have tested all those DE/WM's on top of Ubuntu which in itself adds a lot of stuff not required. Such a test should ideally be done on a netinstall in a VM where you snapshot the base install and then measure each environment.

I tried a variation of this.  In a VM, terminal only install.  Added slim, xorg and openbox.  A boot to openbox shows a 200M increase.  Wonder how I could break this down better, this way isn't working.

---

### Post by oldos2er on 2013-04-14
> **screamingjazz said:**
> I've found this interesting article regarding the amount of memory used by a number of window managers and desktop environments.

[http://l3net.wordpress.com/2013/04/09/a-memory-comparison-of-light-linux-desktops-part-2/](http://l3net.wordpress.com/2013/04/09/a-memory-comparison-of-light-linux-desktops-part-2/)


[This]("http://www.datamation.com/open-source/gnome-or-kde-the-old-question-is-new-today-1.html") is an interesting article along the same lines.

---

### Post by snowpine on 2013-04-14
i have 2gb ram so i use gnome, no problem :)
fluxbox actually runs worse on this laptop b/c it has no power management. i get better battery life and runs cooler with gnome.

---

### Post by ibjsb4 on 2013-04-14
> **snowpine said:**
> i have 2gb ram so i use gnome, no problem :)
fluxbox actually runs worse on this laptop b/c it has no power management. i get better battery life and runs cooler with gnome.

Couldn't laptop-mode-tool just be added to fluxbox or whatever?

---

### Post by snowpine on 2013-04-14
> **ibjsb4 said:**
> Couldn't laptop-mode-tool just be added to fluxbox or whatever?

sure, or i can just use gnome in its default config b/c i have 2gb :)

---

