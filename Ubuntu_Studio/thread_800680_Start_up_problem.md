---
title: "Start up problem"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by misshannah on 2008-05-20
I've recently installed Ubuntu on my laptop and now the majority of the time I start it up it does the ubuntu loading screen then goes black, and never changes to the log in screen. 
When I press the restart button the same thing happens most of the time. But if I reset it by pulling out the battery and then putting it back in it seems to start up just fine. My laptop never did this with windows. 
Is it just a coincidence that it's happened at the same time I intalled Ubuntu?

**just realised I posted this in the wrong section. My bad. Will post it elsewhere.

---

### Post by warbread on 2008-05-20
First, backup your xorg.conf

```
:-$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backuppersonal
```


Then, try booting into recovery mode and typing into the terminal:

```
:-$  sudo dpkg-reconfigure xserver-xorg
```

Just go with the defaults if you don't know what you're doing.  It'll require a little fixing later, so don't be freaked out if it looks like the drivers don't work when you get back in.

If that doesn't work, you can try 

```
 :-$ sudo dpkg-reconfigure gdm
```

From there, we'll see where else we can go.

---

### Post by misshannah on 2008-05-20
Thanks for that, seems to have solved the problem.

---

