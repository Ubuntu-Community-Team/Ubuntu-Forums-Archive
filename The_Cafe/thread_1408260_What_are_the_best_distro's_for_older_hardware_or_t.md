---
title: "What are the best distro's for older hardware or the best way to go about installing?"
date: 2010-02-16
forum: The Cafe
---

### Post by gymophett on 2010-02-16
I'm getting an old computer in not too long. When I get it, I will post the specs. But I bet the ram will only be anywhere from 64mb to 192mb.
Which is sort of a big difference. No matter what the ram. I am going to run it the lightest I can.
I don't know if doing an Ubuntu minimal will be such a good idea, as I don't know how big the HD will be. And I found out the base system isn't big, but bigger than I thought, and there are smaller distros.
The other threads I have seen like this date back to 2006 or have about 4 posts. And much can change in 4 years.
So what would be the best way to go about installing anything on a system with such low specs? What distro? Arch?


EDIT: Arch never would work right for me. I could install the base system. After that was hell.

---

### Post by HermanAB on 2010-02-16
Howdy,

Puppy Linux or Damn Small Linux are probably your only options:
[http://puppylinux.org](http://puppylinux.org)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Yes on 2010-02-16
If you truly want the "lightest" the BasicLinux would be good.

---

### Post by gymophett on 2010-02-16
> **Yes said:**
> If you truly want the "lightest" the BasicLinux would be good.

Ahhh. THANKS MAN! I was going to get this really really old computer alongside my other old one im getting that only boots from floppies, just to see if I could get it running.

---

### Post by mimor on 2010-02-16
You might also be interested in the LFS project ;)
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

> The nice thing is that you learn a lot with this.

---

### Post by scottuss on 2010-02-16
> **mimor said:**
> You might also be interested in the LFS project ;)
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

> The nice thing is that you learn a lot with this.

Yeah but he probably wants a distro that he can use before this old machine starts to disintegrate.... ;)

---

### Post by mimor on 2010-02-16
ok, how about this one?
[http://www.kolibrios.org/](http://www.kolibrios.org/)

---

### Post by koleoptero on 2010-02-16
> **mimor said:**
> ok, how about this one?
[http://www.kolibrios.org/](http://www.kolibrios.org/)

This is a nice choice for the computer that only boots from floppies. I tried it several days ago. Plays mp3 OOTB which is more than ubuntu can say :lolflag:

But for the other computer, if it has 192mbytes of ram you can easily install crunchbang, or an ubuntu karmic minimal + openbox, and it will run easily. If it has 128mbyte or less of ram then it's probably better if you with puppy linux or something similar.

Keeping it light on the apps after you choose the environment is a bit harder. Firefox is not a good idea. Midori or chromium is better imho. Also use console based apps for music like cmus (which I love more than gui players no matter what). There are many good options available.

Post here when you get it and know the computer's exact specs. :)

---

### Post by Jose Catre-Vandis on 2010-02-16
SLiTaZ

(Get the cooking iso for more up to date features)

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)


Xubuntu CLI Install

Get the Alternate CD
Press F4 at boot screen to select CLI install
You will eventually end up with a CLI prompt

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
``` (or similar)

---

### Post by gymophett on 2010-02-16
I think I am going to adjust VirtualBox to seem like a low end old system and see which one of these runs best.

I also found a light one called Tiny Core Linux.

EDIT: This page on Wikipedia is also helpful..   [http://en.wikipedia.org/wiki/Mini_Linux#Desktop_or_CD-distributions_with_installation_option](http://en.wikipedia.org/wiki/Mini_Linux#Desktop_or_CD-distributions_with_installation_option)

---

### Post by NormanFLinux on 2010-02-16
I'd install Xpud or LXDE. Both will work on resource constrained older hardware.

---

### Post by gymophett on 2010-03-03
So the computer I have has 64mb ram and and Intel Pentium 633Mhz.

I'm running Puppy on it right now, and it runs quite well. But I want something even lighter.

---

### Post by Sporkman on 2010-03-03
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by gymophett on 2010-03-03
> **Sporkman said:**
> [http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

I never knew they had such a thing! Thank you so much!

---

### Post by Sporkman on 2010-03-03
> **gymophett said:**
> I never knew they had such a thing! Thank you so much!

Shirley. (Don't call me Shirley!) Distrowatch.com is a good go-to place for distro information.

---

### Post by samalex on 2010-03-03
> **gymophett said:**
> I'm getting an old computer in not too long. When I get it, I will post the specs. But I bet the ram will only be anywhere from 64mb to 192mb.

Actually I've been meaning to ask if anyone knows of a distro of Linux or even Minix that'll run on an 8088 system.  I have an older Tandy 8088 laptop I'd love to use as more of a smart terminal that can telnet into various systems on my network.  Yeah I'll need to find some way to get it networked, but I have some ideas on that.  First just need to find some decent *nix based OS to throw on it.

Sam

---

### Post by Sporkman on 2010-03-03
**samalex:**

These aren't *nix but you can try:

[http://www.sics.se/contiki/about-contiki.html](http://www.sics.se/contiki/about-contiki.html)
[http://www.kolibrios.org/](http://www.kolibrios.org/)

---

### Post by Phrea on 2010-03-03
> **mimor said:**
> ok, how about this one?
[http://www.kolibrios.org/](http://www.kolibrios.org/)

That would work on the computer the OP suggests, but it is by no means a 'light' os, compared to it's single diskette size.

But, I will say that it packs one huge punch !
I bet a lot of us remember the QNX demo disk [also a single diskette os] from way back when, and KolibriOS kicks it's behind ten times over.

---

