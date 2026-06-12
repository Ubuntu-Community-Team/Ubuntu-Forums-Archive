---
title: "How do you use /opt"
date: 2007-06-09
forum: The Cafe
---

### Post by meatpan on 2007-06-09
Well, the title says it all.  What do you put in /opt?   If you know something about the true purpose or history behind this folder, let us know!

---

### Post by mech7 on 2007-06-09
only have xampp in there have no clue what all these dirs are for though to me itls only confusing

---

### Post by FuturePilot on 2007-06-09
I use it to install programs that either aren't in the repos or to install a newer version of a program that is in the repos.
Currently on my Dapper box I have the latest Mozilla build of Firefox and Songbird installed in /opt

I believe the purpose of this directory is to do just that. Install other programs that don't have a place. Most likely ones you installed yourself.
> **/opt**
Used for storing random data that has no other logical destination.
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/]("http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/")

---

### Post by siimo on 2007-06-09
I use it to hide my porn ;)

---

### Post by reacocard on 2007-06-09
I don't use it, in fact, /opt doesn't even exist on my system!

However, [according to wikipedia]("http://en.wikipedia.org/wiki/FHS"):
```
/opt/ 	Optional application software packages.
```

---

### Post by FuturePilot on 2007-06-09
> **reacocard said:**
> I don't use it, in fact, /opt doesn't even exist on my system!
I think that was a bug if you upgraded from the Feisty RC to the Final version as the RC didn't have /opt

---

### Post by reacocard on 2007-06-09
> **FuturePilot said:**
> I think that was a bug if you upgraded from the Feisty RC to the Final version as the RC didn't have /opt

Nope, clean install of feisty stable. I don't really care, /opt is useless for me and having it missing doesn't seem to affect anything.

---

### Post by juxtaposed on 2007-06-09
Nothing; I didn't even know it existed.

I don't put files in odd folders like that. Just anywhere in my home folder (including desktop) and wherever apt puts them.

---

### Post by zenwhen on 2007-06-09
I have Azureus installed in /opt

---

### Post by Nikron on 2007-06-09
Archlinux puts a bunch of things in /opt/, while for some programs like Eclipse and Acroread, this makes sense, but recently **Gnome** got moved out of opt.  It doesn't really effect the user though, because everything is automatically added to their path anyway.

---

### Post by kevinlyfellow on 2007-06-09
In /opt I have mathematica and system76 drivers.  The drivers are there by default (the deb drops them there).  I don't know why I put mathematica in there, probably because I didn't have a deb for it.

---

### Post by meatpan on 2007-06-10
A couple uses for /opt that I have seen:

At work, the /opt directory is a collection of 'non-free' programs that require special licenses.  I think this decision was made to keep all of these programs in a common location, as opposed to mixing them with the baziliion packages in /usr/local.

In school, the IT staff placed all manually (ie, non-aptitude) built programs in /opt.  A clever way to isolate all programs that might have special dependency problems, since they required a custom build.

---

### Post by _simon_ on 2007-06-10
I use it for applications I have manually installed i.e.not with Synaptic.

Currently it has azureus, google-earth, nvu, ies4linux and thunderbird in there.

---

### Post by DoktorSeven on 2007-06-10
Self-contained, Windows-like program installs that I manually install that use their own directory unlike most programs that use the bin/share/lib method.

Examples: Unreal Tournament, Firefox (I compile my own), etc.

---

