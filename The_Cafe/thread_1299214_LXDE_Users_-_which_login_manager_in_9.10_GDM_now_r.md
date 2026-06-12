---
title: "LXDE Users - which login manager in 9.10? GDM now requires GNOME, SLIM vanished...."
date: 2009-10-23
forum: The Cafe
---

### Post by earthpigg on 2009-10-23
Hi,

Five seconds looking at my signature will reveal why I am soliciting input from my fellow LXDE+Ubuntu users :D

Here's the deal with 9.10, login managers, and LXDE, from what I can figure:

-SLiM has [vanished]("http://packages.ubuntu.com/jaunty/slim") from the 9.10 repositories. I'm not sure why.

-The login manager from LXDE, [LXDM]("http://wiki.lxde.org/en/LXDM"), is Alpha.

-[XDM]("http://packages.ubuntu.com/karmic/xdm") is has ***very*** basic functionality.

-[GDM]("http://packages.ubuntu.com/karmic/gdm") now depends on gnome-session. in turn, that requires a few daemons, gnome-panel, metacity, and other stuff. this new GDM also does ***not*** have a GUI tool for configuration like the previous one did.

-[gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") has appeared in the 9.10 repos, which is what we are using in 9.04, and has none of the issues mentioned in the current GDM.

if you are a command-line installer type, which do you intend to use, if any?

if you are not, which would you prefer your LXDE/Ubuntu distribution of choice to use?

---

### Post by Warpnow on 2009-10-23
> **earthpigg said:**
> Hi,

Five seconds looking at my signature will reveal why I am soliciting input from my fellow LXDE+Ubuntu users :D

Here's the deal with 9.10, from what I can figure:

-SLiM has [vanished]("http://packages.ubuntu.com/jaunty/slim") from the 9.10 repositories. I'm not sure why.

-The login manager from LXDE, [LXDM]("http://wiki.lxde.org/en/LXDM"), is Alpha.

-[XDM]("http://packages.ubuntu.com/karmic/xdm") is has ***very*** basic functionality.

-[GDM]("http://packages.ubuntu.com/karmic/gdm") now depends on gnome-session. in turn, that requires a few daemons, gnome-panel, metacity, and other stuff. this new GDM also does ***not*** have a GUI tool for configuration like the previous one did.

-[gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") has appeared in the 9.10 repos, which is what we are using in 9.04, and has none of the issues mentioned in the current GDM.

if you are a command-line installer type, which do you intend to use, if any?

if you are not, which would you prefer your LXDE/Ubuntu distribution of choice to use?

I'd use GDM legacy but have my eye on LXDM and switch over the second its stable.

---

### Post by SunnyRabbiera on 2009-10-23
maybe they should port the older GDM in a separate repo.

---

### Post by Mark76 on 2009-10-23
Do you know how hard it is to actually find the LXDE svn page?

Very.

---

### Post by Warpnow on 2009-10-23
> **Mark76 said:**
> Do you know how hard it is to actually find the LXDE svn page?

Very.

...The download page on lxde.org directly links it...

Whaddaya mean?

---

### Post by Mark76 on 2009-10-23
Okay, I've found it now.

Still won't compile on Ubuntu though

---

### Post by RiceMonster on 2009-10-23
I use startx with anything other than GNOME or KDE. Try it out

---

### Post by Mark76 on 2009-10-24
I did, but pyalsa-audio (which I need for my volume panel applet) won't run under it.

---

### Post by kagashe on 2009-10-24
You can compile from [source]("http://prdownload.berlios.de/slim/slim-1.3.1.tar.gz") or use [Debian Sid Binary]("http://packages.debian.org/sid/slim").

kagashe

---

### Post by jaxxstorm on 2009-10-24
Just recompile SLiM and repackage it, it takes 2 seconds.

I'll probably be making a package for Spri soon, I'll let you know when its done.

---

### Post by Nerd King on 2009-10-24
Just tried out Spri.. very nice, very nice indeed :)

---

### Post by jaxxstorm on 2009-10-24
> **Nerd King said:**
> Just tried out Spri.. very nice, very nice indeed :)

Thanks a lot :)

---

### Post by earthpigg on 2009-10-25
well, here is my progress:

-the [gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") package is broken. if i can figure out exactly why, i will file the bug report. all i know for now is that from a CLI install, this results in a ***broken*** system becaust gdm seems unable to generate certain X11 files:
```
sudo apt-get install xorg gdm-2.20
```

-this also results in a broken system from a CLI install: 
```
sudo apt-get install xorg lxde
```

it tries to pull gdm current, but does not pull the complete set of gnome depends... so gdm is broken.

-combining the above (install xorg gdm-2.20 lxde) also breaks your system.

-so, yeah. both [gdm]("http://packages.ubuntu.com/karmic/gdm") and [gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") are ***essentially broken*** in 9.10.

-slim's .deb pulled from the 9.04 repos works fine in 9.10 after manually resolving depends to make dpkg stfu and install.

-xdm is an option that remains functional OOB (as much as one can claim xdm is 'functional') in 9.10 using 9.10 repos.

---

### Post by jaxxstorm on 2009-10-25
> **earthpigg said:**
> well, here is my progress:

-the [gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") package is broken. if i can figure out exactly why, i will file the bug report. all i know for now is that from a CLI install, this results in a ***broken*** system becaust gdm seems unable to generate certain X11 files:
```
sudo apt-get install xorg gdm-2.20
```

-this also results in a broken system from a CLI install: 
```
sudo apt-get install xorg lxde
```

it tries to pull gdm current, but does not pull the complete set of gnome depends... so gdm is broken.

-combining the above (install xorg gdm-2.20 lxde) also breaks your system.

-so, yeah. both [gdm]("http://packages.ubuntu.com/karmic/gdm") and [gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") are ***essentially broken*** in 9.10.

-slim's .deb pulled from the 9.04 repos works fine in 9.10 after manually resolving depends to make dpkg stfu and install.

-xdm is an option that remains functional OOB (as much as one can claim xdm is 'functional') in 9.10 using 9.10 repos.

I'm not on my Linux box right now, but I don't think SLiM has that many depends does it?

---

### Post by earthpigg on 2009-10-25
> **jaxxstorm said:**
> I'm not on my Linux box right now, but I don't think SLiM has that many depends does it?

nah, reasonable amount. very few. i think they are all included with lxde, but not with xorg.

its been an issue because ive been installing the display manager before lxde because [lxde will pull gdm current]("http://packages.ubuntu.com/karmic/lxde") if one isn't installed first.

---

### Post by Hetor on 2009-10-25
> **earthpigg said:**
> Hi,

-[GDM]("http://packages.ubuntu.com/karmic/gdm") now depends on gnome-session. in turn, that requires a few daemons, gnome-panel, metacity, and other stuff. this new GDM also does ***not*** have a GUI tool for configuration like the previous one did.

-[gdm legacy]("http://packages.ubuntu.com/karmic/gdm-2.20") has appeared in the 9.10 repos, which is what we are using in 9.04, and has none of the issues mentioned in the current GDM.


whaaaat?! Oh my god. Why the hell did they do it?

---

### Post by earthpigg on 2009-10-25
> **Hetor said:**
> whaaaat?! Oh my god. Why the hell did they do it?

beats me.

the general pattern for GNOME seems to be to abandon modularity in favor of super tight integration.

this will affect people that like to use parts of gnome without using the whole thing.

until LXDE advances a bit further, those of us that like to mix and match will face some annoyances. 

here is a non-exhaustive breakdown that i found: [http://wiki.archlinux.org/index.php/Gnome_2.28_Changes](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes)

---

### Post by biffbaxter on 2009-11-01
Easy way to keep slim and minimal on 9.10 is to install lxde-core - this will not pull GDM. installing the lxde meta package will.

Then install the slim .deb from the 9.04 repos. 

lxde-core meets all the dependencies and slim installs with no errors.

Then you have a login manager and LXDE again.

you might want to still go into synaptic and install some of the other lxde goodies that core does not, but at least you will not get all the other "stuff" you dont want.

tks,

biff

---

### Post by SomeGuyDude on 2009-11-01
Am I the only one that has no problem with not having a graphical login at all? Just punch in the credentials, hit "xinit" and I'm good to go.

---

### Post by Exodist on 2009-11-01
> **SomeGuyDude said:**
> Am I the only one that has no problem with not having a graphical login at all? Just punch in the credentials, hit "xinit" and I'm good to go.
I really dont. My wife will trip out tho.

---

### Post by ve4cib on 2009-11-01
I'd second (third?) the suggestion of installing SLIM from either the old repos (download the package and $ dpkg -i ____.deb), or compiling it from source.

Failing that, depending on your needs, XDM may offer sufficient options.  Sure, it's less-customizable, but it'll let you log in graphically in the end.

---

### Post by Warpnow on 2009-11-05
I installed Debian Sid's Slim .deb file from packages.debian.net, and it works fine on ubuntu. Plus, it has auto-login, which the version in jaunty did not.

---

