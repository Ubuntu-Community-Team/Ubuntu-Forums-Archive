---
title: "Distro challenge"
date: 2008-01-01
forum: The Cafe
---

### Post by gn2 on 2008-01-01
I have an old P3 500mhz, 192mb RAM, Toshiba Portege 3440CT.

It has no network adapter, I don't have a floppy drive for it and it can't boot from USB.

It does have a bootable but external Cardbus CD-Rom drive that not all Linux installers can detect.
Live CD's just will not run so it has to be a text installer like the Xubuntu Alternate CD.

Anyone got any suggestions for a lightweight distro bearing in mind the difficulties of the limits on installation methods due to lack of a network adapter, floppy drive and flaky CD-Rom drive?

I've run Xubuntu 7.04 on it, but 7.10 just plain won't run properly.
Vector starts the installation, but won't "see" the CD-Rom drive to copy files from during the install.

Currently I have Zenwalk on it, but are there any good alternatives which would work?

---

### Post by HermanAB on 2008-01-01
Of all the super light distros Puppy Linux is the best.  Otherwise, try Xubuntu.

---

### Post by CCNA_student on 2008-01-01
How about gentoo Linux?

---

### Post by gn2 on 2008-01-01
> **HermanAB said:**
> Of all the super light distros Puppy Linux is the best.

Not had any luck with Puppy getting it installed to hard drive. 

> **HermanAB said:**
>  Otherwise, try Xubuntu.

Xubuntu has been fine, but only as far as 7.04, 7.10 just won't run at a reasonable speed.
Need to find something good for when 7.04 support expires.
Zenwalk 4.8 seems reasonably OK, but Wireless is tricky, won't auto connect with my card, but will work OK when connected manually.

---

### Post by gn2 on 2008-01-01
> **CCNA_student said:**
> How about gentoo Linux?

I'm a dyed in the wool point-and-clicker who will only use CLI reluctantly.

I don't suit Gentoo, it's not the other way round :D

---

### Post by p_quarles on 2008-01-01
Fluxbuntu is lighter than Xubuntu, and comes with a fully-configured setup for point-and-clickers. And it will certain take less time to install than Gentoo. ;)

---

### Post by el_ricardo on 2008-01-01
I was about to suggest zenwalk until i read the last bit of your post lol, its a very good distro for low-end PCs. 

Gentoo could work well but its a biatch to install

crux linux could be good, but the installer requires an internet connection if you want anything other than the base install (which doesn't include a graphical environment)

DSL, or DSL-N frugal install will probably work nicely, although that depends on DSL being able to boot from your CD drive

I have a similarly spec'd laptop, slightly faster CPU and 256MB of RAM, and openSUSE 10.3 runs quite nicely on it, which i was surprised at!

really though, from experience installing on low-end computers, I'd stick with zenwalk, try compiling your own kernel to squeeze a but of extra juice out of it! If you definatly don't want zenwalk, all you can do is download a bunch of different CDs and try them out!

---

### Post by pieisgood4589 on 2008-03-24
> **HermanAB said:**
> Of all the super light distros Puppy Linux is the best.  Otherwise, try Xubuntu.

Are you kidding me? I don't see why people brag about how fast Puppy is on old computers. Dam* (n) Small Linux is so much faster, it runs on 16Mb of RAM, and it's only 50 MB... :)

---

### Post by LaRoza on 2008-03-24
You can use IceWM or JWM with a base install of Ubuntu (use alternative disk of any *buntu)

---

### Post by cardinals_fan on 2008-03-24
Update Zenwalk to 5.0, it'll knock your socks off (I can't believe I just used that expression :) ).  It will actually run very fast (even on those specs) if you use Fluxbox.  Otherwise, install any lightweight distro and use a *box WM.

---

### Post by Vorian Grey on 2008-03-24
If Puppy isn't for you, try DSL.

---

### Post by init1 on 2008-03-24
If not all distros recognize the CD drive, try TTYLinux. It loads to RAM at boot so it will work even if it can't see the drive.

---

### Post by gn2 on 2008-04-25
As an update to this thread, big thanks go to everyone who has posted suggestions, most of which I have tried.
Finally I have decided on a replacement that suits my aging laptop, it's Xubuntu 8.04 RC.
Runs so much better than 7.10 did, so a big thank-you to all the 8.04 developers from me. 

I would suggest that anyone who gave up on Xubuntu 7.10 with older hardware should give 8.04 a go, the difference is just amazing.

---

