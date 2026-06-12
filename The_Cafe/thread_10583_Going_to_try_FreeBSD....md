---
title: "Going to try FreeBSD..."
date: 2005-01-09
forum: The Cafe
---

### Post by jdong on 2005-01-09
In light of the recent security issues with Linux, and my curiousity, I've decided to give FreeBSD another try. The last one was an embarrassing encounter with lack-of-knowledge and such fun!

Test system: AMD k6 266MHz laptop! I need this to do microcontroller programming for Robotics.

Desired functionality:

Well, what I need the most is **wine**. From what I see, there are binaries for 20040505, which I'm likely to just stick with. I could build it from ports, if I had that much free time on my hand!

X will also be well-appreciated. I want Fluxbox at least -- perhaps I'll also get XFCE, but that's completely optional.

---

### Post by tiiim on 2005-01-09
[QUOTE=jdong]In light of the recent security issues with Linux, and my curiousity, I've decided to give FreeBSD another try. The last one was an embarrassing encounter with lack-of-knowledge and such fun!

Test system: AMD k6 266MHz laptop! I need this to do microcontroller programming for Robotics.

Desired functionality:

Well, what I need the most is **wine**. From what I see, there are binaries for 20040505, which I'm likely to just stick with. I could build it from ports, if I had that much free time on my hand!

X will also be well-appreciated. I want Fluxbox at least -- perhaps I'll also get XFCE, but that's completely optional.[/QUOTE]
 let us know how it goes im currently seeing what system will suit me and FreeBSD is on my testing list so i personally will be interested to see what its like as well. Ubuntu on top of my Linux list at least the power of apt-get is that you get the lastest sucrity update very quickly.

---

### Post by Quest-Master on 2005-01-09
Security issues with Linux..? Is there something I've been missing?

---

### Post by Quake on 2005-01-09
Local Root Exploit in Linux 2.4 and 2.6
[http://linux.slashdot.org/article.pl?sid=05/01/07/2028203&from=rss](http://linux.slashdot.org/article.pl?sid=05/01/07/2028203&from=rss)

---

### Post by Quest-Master on 2005-01-09
Oh, yeah.

Well, it's going to be fixed soon. :)

---

### Post by wallijonn on 2005-01-09
jdong,

How many local users have access to your machine and how many have the expertise to exploit the vulnerability?

---

### Post by tiiim on 2005-01-09
[QUOTE=wallijonn]jdong,

How many local users have access to your machine and how many have the expertise to exploit the vulnerability?[/QUOTE]
 lol im gonna also try freebsd for a laugh something to do eh ;) nothing to do with the security issue cos i dont have that problem but just for laugh been reading up on it sounds very good. But i keep Ubuntu on my laptop though :D

---

### Post by Lovechild on 2005-01-09
FreeBSD is an interesting OS, I especially like their scheduler entity threading, it seems logical to do thread assisted scheduling, time will tell if this truly is a superior solution.

But FreeBSD sadly lacks features like HAL support, which make it unsuited for my desktop, but other than that I have used FreeBSD in various setups for quite a long time and have grown to love the level of documentation they enforce on the system.

---

### Post by poofyhairguy on 2005-01-10
[QUOTE=jdong]
X will also be well-appreciated. I want Fluxbox at least -- perhaps I'll also get XFCE, but that's completely optional.[/QUOTE]

MMMM....Xfce....basically Gnome-lite.

---

### Post by jdong on 2005-01-12
Ok, I've switched directions, and installed a FBSD dual-boot on my Athlon64 desktop (running i386 arch).

I have KDE 3.3.0 installed, basics configured. Top priorities now:

1. Get Firefox 1.0
2. Get 3D NVidia
3. Upgrade all upgradable ports
4. Get sound working


So far, I like BSD's speed. While at a desktop, it feels exactly like a more responsive Linux! Under high loads, I am seeing BSD more desktop-responsive!

I'm being seriously annoyed by FBSD's differing directory structure. For example, xorg.conf is in /usr/X11R6/lib/xorg.conf... who would've thought?? Oh well, I'll get used to it.


I think I'll keep FreeBSD on this system alongside Ubuntu. Screw SuSE.

---

### Post by tiiim on 2005-01-12
[QUOTE=jdong]Ok, I've switched directions, and installed a FBSD dual-boot on my Athlon64 desktop (running i386 arch).

I have KDE 3.3.0 installed, basics configured. Top priorities now:

1. Get Firefox 1.0
2. Get 3D NVidia
3. Upgrade all upgradable ports
4. Get sound working


So far, I like BSD's speed. While at a desktop, it feels exactly like a more responsive Linux! Under high loads, I am seeing BSD more desktop-responsive!

I'm being seriously annoyed by FBSD's differing directory structure. For example, xorg.conf is in /usr/X11R6/lib/xorg.conf... who would've thought?? Oh well, I'll get used to it.


I think I'll keep FreeBSD on this system alongside Ubuntu. Screw SuSE.[/QUOTE]
 i be installing freebsd soon as well I been reading "the manually" and just ordered it in book form and ordered the cds i been reading up on freeBSD seems a great system. Im gonna give it a try but keep Ubuntu on my laptop.

---

### Post by jdodson on 2005-01-12
[QUOTE=Quest-Master]Oh, yeah.

Well, it's going to be fixed soon. :)[/QUOTE]

if youve updated warty lately(past few days) you are already fixed.  if you notice the choices in the kernels, the old one is the "insecure" one the new one is patched.

the ubuntu security folks had this patched in a day or so.

---

