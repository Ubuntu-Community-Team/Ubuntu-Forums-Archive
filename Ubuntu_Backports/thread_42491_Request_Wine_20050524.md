---
title: "Request: Wine 20050524"
date: 2005-06-17
forum: Ubuntu Backports
---

### Post by abandoned_hussam on 2005-06-17
There's wine 20050524(or something like that ) in debian testing. 
Can you guys please backport this from Debian repositories?

---

### Post by Moobert on 2005-06-17
That verson can be found from the main site, add this to /etc/apt/sources.list
```

#wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```

---

### Post by abandoned_hussam on 2005-06-17
thanks I did that. Worked properly. :)

---

### Post by Moobert on 2005-06-18
[QUOTE=ht990332]thanks I did that. Worked properly. :)[/QUOTE]

Cool, but that source is abit random with its updates.

If you can't find a deb though:
[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)
that cvs script is better wine at following wine updates... also has stuff lke the dx9 builds.

---

### Post by kb00heda on 2005-06-18
I haven't tried it yet, and perhaps I won't (my Wine works quite nicely as it is), but they seem to have Ubuntu repositories as well? I tested

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) hoary/

in my source list, which updated, and prompted upgrades for wine, libwine, and winetools. There are Warty and Breezy folders too. Are there drawbacks of using those instead?

---

### Post by McQuaid on 2005-06-19
I don't know too much about wine but thought it was good that they had hoary packages, however it seems that it's a bare bones version of wine.  What about various packages like libwinegl for opengl support and libwine-alsa etc.  Is it ok to mix match these?  Are those others not usually updated along with the core packages?

I was going to install this updated version but I think I'll hold off til I know more.

---

### Post by jdong on 2005-06-20
There's two flavors of wine packages:

1) WineHQ's APT repo at wine.sf.net
2) Traditional Debian

I've been using 1) for all the Warty Backports versions , because 2 has been outdated for quite a while. However, Hoary's making a comeback with 2, so I've kept with it. They both are the same WINE, just packaged differently. WineHQ's version put all the libwine-* into the main package.

---

