---
title: "A question about GNOME version in Ubuntu 12.04"
date: 2011-11-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Starlight on 2011-11-27
Hi! I've read [this article]("http://www.omgubuntu.co.uk/2011/11/precisely-what-gnome-version-will-be-in-ubuntu-12-04/") which said that Ubuntu 12.04 won't have full GNOME 3.4, only some 3.4 programs. Even though I like Unity, for now Gnome Shell is much easier and nicer to use for me, so I'd love to have a full GNOME desktop. Right now I'm using Fedora for that, but I'm thinking about switching back to Ubuntu, because unfortunately there is some stuff that isn't packaged for Fedora. :( So, does anyone know if it will be possible to have a full and stable GNOME 3.4 desktop on 12.04 if I use the [Gnome 3 ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3")? :)

edit: just to clarify, of course I mean the final version of Ubuntu 12.04 when it's released, not the current development version :)

---

### Post by Harry33 on 2011-11-27
> **Starlight said:**
> Hi! I've read [this article]("http://www.omgubuntu.co.uk/2011/11/precisely-what-gnome-version-will-be-in-ubuntu-12-04/") which said that Ubuntu 12.04 won't have full GNOME 3.4, only some 3.4 programs. Even though I like Unity, for now Gnome Shell is much easier and nicer to use for me, so I'd love to have a full GNOME desktop. Right now I'm using Fedora for that, but I'm thinking about switching back to Ubuntu, because unfortunately there is some stuff that isn't packaged for Fedora. :( So, does anyone know if it will be possible to have a full and stable GNOME 3.4 desktop on 12.04 if I use the [Gnome 3 ppa]("https://launchpad.net/%7Egnome3-team/+archive/gnome3")? :)

You may want to use both Ricotz Gnome-shell Testing PPA and Gnome 3 Team PPA to be on the edge of the development leading to Gnome 3.4.

However, bear in mind the warnings on those PPA's.

---

### Post by Starlight on 2011-11-27
> **Harry33 said:**
> You may want to use both Ricotz Gnome-shell Testing PPA and Gnome 3 Team PPA to be on the edge of the development leading to Gnome 3.4.

However, bear in mind the warnings on those PPA's.

Thanks for the answer! :) But I didn't mean using any development versions, what I meant is the final, stable version of Gnome 3.4 on the final, stable version of Ubuntu 12.04 when it's released. :)

---

### Post by Harry33 on 2011-11-27
> **Starlight said:**
> Thanks for the answer! :) But I didn't mean using any development versions, what I meant is the final, stable version of Gnome 3.4 on the final, stable version of Ubuntu 12.04 when it's released. :)

The PPA's I mentioned are up now. Only the owner of those PPA's knows for how long.
I don't.

However, we know that Ubuntu PP 12.04 LTS will (when released on 26th April 2012) not have the whole Gnome 3.4. Also, we know that the default shell will be Unity, not Gnome-shell.

---

### Post by buzzmandt on 2011-11-27
and we also know that gnome-shell is just a simple s*udo apt-get install gnome-shell* away :)

---

### Post by dmoconnell on 2011-11-27
Hi Starlight. To answer your question (which I believe is weather or not you can use the FULL Gnome 3.4 and not parts of Gnome 3.4 ,3.2(3.3?) and Gnome Shell) Yes you can. Just add the Gnome PPA that you have and I believe that all thats need to do is run sudo apt-get update && sudo apt-get upgrade (I believe that is correct) 
I believe Philinux would know the full correct answer (I'll PM him a link to this thread and ask if he wouldn't mind weighting in)

Dm

---

### Post by cariboo on 2011-11-28
Precise will use GTK3.4, but most of the apps will still be based on Gnome 3.2, as Gnome 3.4 will be released only a month before Precise, so there won't be a lot of time to include the newer versioned apps.

---

### Post by vasa1 on 2011-11-28
> **cariboo907 said:**
> Precise will use GTK3.4, but most of the apps will still be based on Gnome 3.2, as Gnome 3.4 will be released only a month before Precise, so there won't be a lot of time to include the newer versioned apps.

So will we still have gtk-2.0 and gtk3.0 or will gtk-2.0 be gone for good?

---

### Post by Harry33 on 2011-11-28
> **vasa1 said:**
> So will we still have gtk-2.0 and gtk3.0 or will gtk-2.0 be gone for good?

Gnome Desktop Environment (Gnome) is not actually the same as Gimp Tool Kit (GTK).
Almost all the applications outside Gnome 3 (Brasero etc..) only work on GTK+2 (like Firefox, Thunderbrid, LibreOffice ...).

This will be the situation for quite a long time. In the mean time, we need GTK+2.

---

### Post by philinux on 2011-11-28
> **cariboo907 said:**
> Precise will use GTK3.4, but most of the apps will still be based on Gnome 3.2, as Gnome 3.4 will be released only a month before Precise, so there won't be a lot of time to include the newer versioned apps.

Cariboo is spot on as usual.

At this stage it's a case of wait and see over the coming months. Whatever the outcome of what is in the archives at release time there is always the GNOME 3 Team PPA. And of course backports as time goes on.

Anyone can also ask the developers directly.
[http://design.canonical.com/2011/11/getting-in-touch-with-us/](http://design.canonical.com/2011/11/getting-in-touch-with-us/)

---

### Post by jbicha on 2011-11-28
Yes, GNOME 3.4 will be available in the GNOME3 PPA, just like the parts of GNOME 3.2 that didn't make it into 11.10 are in the PPA. Canonical's Desktop Team will be focusing on what actually ships in 12.04 (which is likely to include quite a bit of 3.4) so especially this early, we can't guarantee that all of 3.4 will be in the PPA when 12.04 is released but it should happen shortly afterwards if it's not done in time.

---

### Post by vasa1 on 2011-11-28
> **Harry33 said:**
> Gnome Desktop Environment (Gnome) is not actually the same as Gimp Tool Kit (GTK).
Almost all the applications outside Gnome 3 (Brasero etc..) only work on GTK+2 (like Firefox, Thunderbrid, LibreOffice ...).

This will be the situation for quite a long time. In the mean time, we need GTK+2.

Thank you for explaining, Harry33! It's a bit hard for newcomers to understand the subtleties :)

---

### Post by Harry33 on 2011-11-28
> **vasa1 said:**
> Thank you for explaining, Harry33! It's a bit hard for newcomers to understand the subtleties :)

:guitar: You are welcome.

---

