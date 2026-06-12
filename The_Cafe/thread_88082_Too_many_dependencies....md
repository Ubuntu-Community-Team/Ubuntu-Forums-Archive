---
title: "Too many dependencies..."
date: 2005-11-09
forum: The Cafe
---

### Post by foxy123 on 2005-11-09
The one of the very few things which annoys me in Linux is too many dependencies in applications. What I mean by that is the following. If you are a happy to use say KDE and only KDE apps, it's ok. But I use for example XFCE as a DE and apps from gnome and kde like amarok, gaim etc. Also I like latest version of things, meaning that I occasionally comple things from source (like amarok). Well I usually end up with almost full install of GNOME and KDE in addition to XFCE.

I guess it's a price to pay for the variety. But the problem is that I still have a lot of apps installed as dependencies which I never use. Let's look in my menu: kate, kjobviewer, ksysguard, noatun etc, leaving alone all those libs. I wonder if there is a more efficient way to do things? Could all the apps be DE independent?

---

### Post by Stormy Eyes on 2005-11-09
[QUOTE=foxy123]Could all the apps be DE independent?[/QUOTE]

Yes, but the developers would have to reinvents a great many wheels. Hard disk space is pretty cheap. Why not just edit your menu to remove apps you do not want to see and forget about them if you've got disk to spare? That's what I do.

---

### Post by foxy123 on 2005-11-15
[QUOTE=Stormy Eyes]Yes, but the developers would have to reinvents a great many wheels. Hard disk space is pretty cheap. Why not just edit your menu to remove apps you do not want to see and forget about them if you've got disk to spare? That's what I do.[/QUOTE]
Well I just wondering about some cases. For example Kate - a simple text editor, there are lots of them. It's been installed as dependency. So if I want to remove it, I have to remove kde-core, kde-devel, kdebase and kdebase-dev. I do not believe that all those components cannot live without kate. I have to install a full KDE just to compile amarok. Isn't is rediculous? A full DE gets a lot of space I guess.

---

### Post by ssam on 2005-11-15
There are a few case were the dependancies are propbably unnecissary, either by policy (like ubuntu-desktop depending on evolation) or by relic of old design (the monolithic X11 builds (which are being phased out)).

actually the dependancy thing saves disk space/bandwidth/ram when used properly. If each gnome application had all the gtk library (and everything else) rolled into it (i think this is called a static build) then it could run on its own, but it would be huge. If you ran two static gnome apps then you would have gtk in ram twice. (this might be a slight simplification, but its roughly true). also if a bug was found in a low level library then everything that uses it would have to be recompile and downloaded.

---

### Post by foxy123 on 2005-11-15
[QUOTE=ssam]There are a few case were the dependancies are propbably unnecissary, either by policy (like ubuntu-desktop depending on evolation) or by relic of old design (the monolithic X11 builds (which are being phased out)).

actually the dependancy thing saves disk space/bandwidth/ram when used properly. If each gnome application had all the gtk library (and everything else) rolled into it (i think this is called a static build) then it could run on its own, but it would be huge. If you ran two static gnome apps then you would have gtk in ram twice. (this might be a slight simplification, but its roughly true). also if a bug was found in a low level library then everything that uses it would have to be recompile and downloaded.[/QUOTE]
I agree about libraries. If several apps use the same library it does not make sense to have it several times uploaded into memory. But kate? Why the whole DE depends on Kate? Gedit removal does not require to remove the core components of Gnome. I wonder if it is mostly KDE thing?

---

### Post by Pablo_Escobar on 2005-11-15
Heh, about mentioned package : kate -> kde-core -> Description This **metapackage** includes the core official modules released with KDE.

I don't know if this is the case (I'm not a KDE user), but there are some **metapackages** like ubuntu-desktop, which are just a list of packages which should be included. They are solely for maintenance purpouse.
I had in my Ubuntu evolution removed, all the strange fonts. Ubuntu-desktop was removed as well. 
My system works without it without a flaw :)
The only reason for it to be is when You dist-upgrade to another release (but that is no problem just install the removed metapackages with dependencies and You're set :) )

---

