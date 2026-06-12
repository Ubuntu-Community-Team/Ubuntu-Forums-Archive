---
title: "Been trying out BSD lately."
date: 2010-10-21
forum: The Cafe
---

### Post by kaldor on 2010-10-21
I've been using BSD on virtualbox for the last few days. Started with FreeBSD, then Midnight and then PC-BSD.

Overall, awesome experience. It actually feels more mature than Linux.

- I'm considering replacing Ubuntu with Midnight or NetBSD on my local "garbage dump" server. I was amazed when I set the RAM to 20 MB on virtualbox and it ran Midnight without a hiccup.

- PC-BSD has two options on the installer; PC-BSD installation or FreeBSD installation. DVD doubles as two distinct setups... cool. 

- Ports is awesome.  

- Linux compatibility is useful.

- PC-BSD had one of the best installers I ever used.

- csh instead of bash. Not much difference, easy to use, and bash available if you really want it.

- GNOME, KDE ports available. 

- Ports/package management just as easy as on Debian/Ubuntu/whatever.

Why isn't this family of operating systems more popular? It makes a wonderful server OS (MidnightBSD makes that easy for newcomers, imo) and even makes a decent desktop OS depending on your needs. The only thing that I can think of is lack of vendor support. The fact it can run on such ancient hardware specs makes it rival DSL and Tinycore for me.

It also feels more stable. I haven't had a single issue running any of the *BSDs in VirtualBox, while some Linux distros fail totally. 

Who else likes BSD?

---

### Post by CharlesA on 2010-10-21
*raises hand*

I've played around with it, but haven't had a huge amount of time to mess around all that much.

---

### Post by juancarlospaco on 2010-10-21
Try Debian BSD and post again...  apt-get powa!

---

### Post by NightwishFan on 2010-10-21
Yes, Debian BSD is pretty cool, and has a lot of packages. I tried it myself, can't wait for it to go stable.

Though Linux is not bad itself. My server boots using 14mb of ram using Ubuntu 10.04.

---

### Post by conundrumx on 2010-10-21
I like BSD, but I **hate** ports.  Maybe I'm missing something, but having to do a locate, then cd, then make install is asinine.

---

### Post by chris200x9 on 2010-10-21
> **conundrumx said:**
> I like BSD, but I **hate** ports.  Maybe I'm missing something, but having to do a locate, then cd, then make install is asinine.

ports is like portage with less breakage and more "make install clean"ing

---

### Post by Cuddles McKitten on 2010-10-21
> **conundrumx said:**
> I like BSD, but I **hate** ports.  Maybe I'm missing something, but having to do a locate, then cd, then make install is asinine.

For people who are building packages, that's much, much easier than any other alternative.  On OpenBSD (might be different for the others) you also have the simpler option of auto-installing the pre-built packages from mirrors which is very similar to apt-get or yum.

---

### Post by perspectoff on 2010-10-21
> **kaldor said:**
> I've been using BSD on virtualbox for the last few days. Started with FreeBSD, then Midnight and then PC-BSD.

Overall, awesome experience. It actually feels more mature than Linux.

- I'm considering replacing Ubuntu with Midnight or NetBSD on my local "garbage dump" server. I was amazed when I set the RAM to 20 MB on virtualbox and it ran Midnight without a hiccup.

- PC-BSD has two options on the installer; PC-BSD installation or FreeBSD installation. DVD doubles as two distinct setups... cool. 

- Ports is awesome.  

- Linux compatibility is useful.

- PC-BSD had one of the best installers I ever used.

- csh instead of bash. Not much difference, easy to use, and bash available if you really want it.

- GNOME, KDE ports available. 

- Ports/package management just as easy as on Debian/Ubuntu/whatever.

Why isn't this family of operating systems more popular? It makes a wonderful server OS (MidnightBSD makes that easy for newcomers, imo) and even makes a decent desktop OS depending on your needs. The only thing that I can think of is lack of vendor support. The fact it can run on such ancient hardware specs makes it rival DSL and Tinycore for me.

It also feels more stable. I haven't had a single issue running any of the *BSDs in VirtualBox, while some Linux distros fail totally. 

Who else likes BSD?

Oh yes. for servers, FreeBSD is venerable, stable, reliable and has been for years. (There's a reason Apple modified BSD for use as OS X).

However, it has a steep learning curve. BSD has long been the province of *nix aficionadoes. The Debian revolution (of which Ubuntu is currently the flagship), though, is built on packaging and marketing to the masses, which has not been a priority for BSD.

Evolution comes from population pressures, and Ubuntu is evolving quite rapidly as the population of users increases exponentially.

Some suggest, however, that Ubuntu is starting to hide the things that *nix aficionadoes find most important in the interest of "appealing to the masses" and "simplifying things." That may eventually alienate power users if it goes too far (as often happens in both the Windows and Mac worlds).

BSD is well-suited to its niche(s), but certainly it has had a different focus. Should Ubuntu go too far down the Windows/Apple "user experience" road, BSD may increasingly emerge as a power-user's choice.

Hmmm, Debian BSD? Sounds quite interesting. A blend of the Debian and BSD ecosystems?

---

### Post by nikstard on 2010-10-21
I've been using FreeBSD on and off for a while, this week I've been dual booting it with Windows 7. Previously used mostly Ubuntu. I appreciate the good documentation, developer orientedness and being a more traditional Unix without all the whizbang. I pretty much live in Emacs and Firefox and use a tiling windows manager. It's nice. Ubuntu is nice too, but I don't really need any of the eye-candy or other stuff aimed mostly at new users and/or non-developers.


> **perspectoff said:**
> 
Hmmm, Debian BSD? Sounds quite interesting. A blend of the Debian and BSD ecosystems?

I think he means Debian GNU/kFreeBSD:

[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

---

