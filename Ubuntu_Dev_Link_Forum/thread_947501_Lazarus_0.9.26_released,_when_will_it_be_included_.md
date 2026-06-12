---
title: "Lazarus 0.9.26 released, when will it be included in the repository?"
date: 2008-10-14
forum: Ubuntu Dev Link Forum
---

### Post by efikkan on 2008-10-14
Lazarus 0.9.26 was finally released today, after almost a year since the previous version.

The deb files on sourceforge works fine with Ubuntu 8.04, but users have to manually install all the debs in the right order.

It would be nice of you compiled Lazarus in GTK 2, so it would smoother with Ubuntu.

This thread might be posted in the wrong category, feel free to move it.

Thanks.

Greetings,
efikkan.

---

### Post by mariuz on 2008-10-18
you can use the official lazarus/fpc repository 
and it will install latest lazarus 0.9.26 and fpc 2.2.0

[http://mapopa.blogspot.com/2008/10/upgrading-to-lazarus-0.html](http://mapopa.blogspot.com/2008/10/upgrading-to-lazarus-0.html)

i wish the changes to ubuntu repositories to be done faster
and i think the core distro can stay unchanged a little bit longer 
but some apps should and must move faster than the rest of the distro 
like:openoffice , firebird 2.1, lazarus , fpc

because stable releases are already there and the intrepid is already dated at the release

also i think the gentoo ideea with continuous upgrade to be good 
at least for me is better to have latest stable applications and kernel 

also backports in ubuntu is completely broken so is better to use the next release or debian experimental to be up to date with all apps

---

### Post by nhandler on 2008-10-25
lazarus 0.9.26 is in Debian unstable. Since no changes have been made to lazarus in Ubuntu, it should be automatically synced once the Jaunty repositories open up. Intrepid is scheduled to be released in under a week. I would suggest just waiting until Jaunty for lazarus 0.9.26, or downloading the deb from sourceforge.

---

### Post by pladam on 2008-11-19
Lazarus appears to be awesome except it hurts my eyes with the default GTK 1 theme.  Bleh.  Anyone know how to make it pretty?

---

### Post by Svenstaro on 2008-11-19
> **pladam said:**
> Lazarus appears to be awesome except it hurts my eyes with the default GTK 1 theme.  Bleh.  Anyone know how to make it pretty?

You have to select "Build Lazarus" from one of the menus and configure it to rebuild itself using GTK2. Quite easy and works well usually.

---

