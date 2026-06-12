---
title: "So Much Gnome in Xubuntu"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Peripheral Visionary on 2012-03-22
I wonder why Xubu has so much Gnome stuff in it? Id it there because it's needed for functionality or is it there to offer additional features that Xfce doesn't?

I'm delighted to find a modern distro that still fits on a CD (my old computer won't boot from a DVD but it likes CDs), so **I'm not complaining**, just very curious. Is all that Gnome stuff really necessary? I'm asking because just for grins I'm trying [another Xfce distro]("http://www.salixos.org/wiki/index.php/Home") out and *it runs as fast from the LiveCD as Xubu does installed to the hard drive!*

Just curious, thanks.

---

### Post by mr_pouit on 2012-03-22
Hi,

Could you list the apps you're considering as gnome stuff? (e.g. for file-roller and evince, there's no really maintained non gnome equivalent...)
Anyway, new suggestions and app comparisons are always appreciated by the Xubuntu team. :P

---

### Post by Peripheral Visionary on 2012-03-22
Gnome-support for Firefox, T-Bird, and Seamonkey; Gnome icon theme, Gnome-this and gnome-that. I'm a newbie so I really don't know if they're needed, and Xubu 12.04 runs fine with all that stuff in there anyway, but I'm curious about why it's needed - and if not needed, why include it? I read a lot to learn as much as I can about Linux, and I have read about a zillion references to Xubu being referred to as "even more bloated than regular Ubuntu" and such. If Xfce is the default desktop, why all that Gnome stuff?

Sorry if it's a newbie question, and if there's a way to make it speed up (because Xfce is supposed to be light and fast compared to Gnome) by removing unnecessary Gnome stuff, please tell me how.

Thanks! This community here is really good for a newbie.

---

### Post by grahammechanical on 2012-03-22
Ubuntu is based on Debian and Gnome.

What is Xubuntu based upon? Ubuntu!

> Xubuntu's goals are to:

provide an easy to use distribution, based on Ubuntu, **using Xfce as the graphical desktop**, with a focus on integration, usability and performance, with a particular focus on low memory footprint. The integration in Xubuntu is at a configuration level, a toolkit level, and matching the underlying technology beneath the desktop in Ubuntu.

[http://en.wikipedia.org/wiki/Xubuntu]("http://en.wikipedia.org/wiki/Xubuntu")

You will notice that even though Unity is the user interface in Ubuntu there is a lot of Gnome stuff in there as well.

Regards.

---

### Post by teachop on 2012-03-22
Xfce4 uses gtk, so gnome parts naturally come along, and as you flesh out a system, gnome is the natural source to pull from.  Xubuntu is not a "light" distro, it is a very complete Xfce4 setup.  On a laptop I built an Xfce4 from scratch using Arch Linux, and learned that a pretty light system can be accomplished, but as I filled in the pieces to get what I was used to from an Ubuntu flavor, pretty much all the gnome libraries etc come along.  That is OK.

The Xfce old school interface is more productive for me than the newer thinking (yes I have spent considerable time with Unity).  Thunar isn't quite as nice as Nautilus, but it is possible to get close with the custom actions and plugins.  (you can run nautilus too if desired, just disable desktop support in it)

Yes there is a lot of gnome in there, but it has the interface style I prefer.  And in my opinion, Xubuntu with the shimmer greybird theme is the most attractive 'buntu right now by far.

---

### Post by Peripheral Visionary on 2012-03-22
> **teachop said:**
> Xfce4 uses gtk, so gnome parts naturally come along, and as you flesh out a system, gnome is the natural source to pull from.  Xubuntu is not a "light" distro, it is a very complete Xfce4 setup.  

It sure is! Gorgeous, functional, simple, elegant! Lots to love. And it runs fine even on my little 512 RAM Celeron 8-year-old Dell. Well, a tad slower with today's updates.

So **gtk is the "culprit"** because both Xfce and Gnome use it - and Gnome is the place to look for the cool **gtk stuff** that makes Xubu so awesome, right? That's what it sounds like you're saying, and it makes sense.

> **teachop said:**
> The Xfce old school interface is more productive for me than the newer thinking (yes I have spent considerable time with Unity).  <snippety> Yes there is a lot of gnome in there, but it has the interface style I prefer.  And in my opinion, Xubuntu with the shimmer greybird theme is the most attractive 'buntu right now by far.

The only "old school" I know is from Xubu 10.04 which was the installed OS on this computer I inherited. It had PCManFM on it in place of Thunar, and I like it better, so I've installed it on my 12.04. I guess "borrowing" from other DEs is pretty common anyway.

Thanks for the explanation! I'll await a few more opinions before I mark this thread SOLVED.

Thanks!

---

### Post by mr_pouit on 2012-03-22
> **Peripheral Visionary said:**
> Gnome-support for Firefox, T-Bird, and Seamonkey; Gnome icon theme, Gnome-this and gnome-that.

For example, firefox-gnome-support "allows Firefox to take advantage of technologies such as GConf, GIO libnotify". Indeed, we don't really use GConf, but GIO and libnotify are not gnome-specific, so we want them.

Similarly for gnome-icon-theme, this is set by Ubuntu to be the fallback icon theme with gtk3 (if it can't find an icon in your current theme it will search in the fallback theme). So we want it too.

It's often for these reasons, although it's always possible that one unneeded gnome app is included by mistake...

> **Peripheral Visionary said:**
> 
I'm a newbie so I really don't know if they're needed, and Xubu 12.04 runs fine with all that stuff in there anyway, but I'm curious about why it's needed - and if not needed, why include it? I read a lot to learn as much as I can about Linux, and I have read about a zillion references to Xubu being referred to as "even more bloated than regular Ubuntu" and such.


You lose some features/integration, but it won't break your desktop if these packages aren't installed. The Xubuntu team tries to provide an integrated desktop environment (and some people think that integration == bloat). Obviously you can't please everyone. :P

---

