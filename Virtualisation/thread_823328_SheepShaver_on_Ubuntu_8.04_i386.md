---
title: "SheepShaver on Ubuntu 8.04 i386"
date: 2008-06-09
forum: Virtualisation
---

### Post by chungy on 2008-06-09
(I know this isn't virtualization, but I'm guessing this is the best category to put this topic)

Basically, I'm trying to make a build myself using the instructions provied on the website: [http://sheepshaver.cebix.net/](http://sheepshaver.cebix.net/) (Checking out CVS, ./autogen.sh, make...)
However, I keep hitting this roadbump.  The actual emulator won't do anything, it will only display this: [http://img265.imageshack.us/img265/4064/screenshotsheepshaveryu4.png](http://img265.imageshack.us/img265/4064/screenshotsheepshaveryu4.png)

Now the reason that I can eliminate the possibility of a bad ROM or bad install disc, is that I can get a version of SheepShaver running by downloading the RPM from this site and using alien+dpkg to install it: [http://gwenole.beauchesne.info/en/projects/sheepshaver](http://gwenole.beauchesne.info/en/projects/sheepshaver)
It seems to run fine this way, but I would be more comfortable getting a native build to work, it feels less dirty (if that makes sense, heh).  This is what I see installing from that RPM: [http://img529.imageshack.us/img529/5256/sheepshaverrpmze3.png](http://img529.imageshack.us/img529/5256/sheepshaverrpmze3.png)

I don't really know if anything more information needs to be said :/

---

### Post by chungy on 2008-06-09
bump?

---

### Post by prshah on 2008-06-10
> **chungy said:**
> 
The actual emulator won't do anything, it will only display this: [http://img265.imageshack.us/img265/4064/screenshotsheepshaveryu4.png](http://img265.imageshack.us/img265/4064/screenshotsheepshaveryu4.png)


I don't know about SheepSaver and such, but the screenshot shown looks like a basic xinit screen, which is how X looks when it loads without a window manager.

Maybe this indicates a window manager problem?

If you got this type of screen in ubuntu, you'd probably try starting the window manager thus:
Switch to a virtual terminal with Ctrl+Alt+F1, login, give the command
```

sudo /etc/init.d/gdm start
```
, then when you get the [OK], switch back with Ctrl_Alt_F7.

---

### Post by chungy on 2008-06-10
No, that has nothing to do with it.  It's the screen a Mac displays when it has no bootable medium... which means something in SheepShaver isn't starting the operating system like it should.

---

