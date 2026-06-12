---
title: "Wasn't Edgy supposed to introduce AIGLX?"
date: 2006-10-26
forum: The Cafe
---

### Post by matthias_k on 2006-10-26
Wasn't AIGLX and its integration into Metacity (by default!) be supposed to be THE feature of Edgy (at least on the desktop, upstart was of course another one).

I didn't read anything about it in the release announcement.

---

### Post by Wolki on 2006-10-26
> **matthias_k said:**
> Wasn't AIGLX and its integration into Metacity (by default!) be supposed to be THE feature of Edgy (at least on the desktop, upstart was of course another one).

AIGLX is enabled by default.

A compositor using AIGLX is, however, not in AIGLX. It basically exists, but is not compiled into edgy for build reasons and because it does not work in general.

I'm also unure whether there will ever be a working compositor in Metacity... right now noone seems to be working on it.

---

### Post by PriceChild on 2006-10-26
AIGLX is in edgy... there's just nothing to use it installed by default ;)

I think that a compositing metacity is in the pipe line.

Please remember though that ubuntu is meant to be scalable for a large base of hardware. Low-end machines just wouldn't function if this were default.

Follow my howto to install beryl or another's to install compiz if you want.

---

### Post by bruce89 on 2006-10-26
> **Wolki said:**
> I'm also unure whether there will ever be a working compositor in Metacity... right now noone seems to be working on it.

[http://cvs.gnome.org/viewcvs/metacity/src/compositor.c?view=markup](http://cvs.gnome.org/viewcvs/metacity/src/compositor.c?view=markup)

---

### Post by jdong on 2006-10-26
The underpinnings (AIGLX) is already enabled in Edgy by default (kind of annoying for fglrx'ers but that's another can of worms)

It's just that there is no compositing manager enabled by default. There is compiz in the official repositories that works with AIGLX, so you can get started with 3d desktop right from Ubuntu repositories.

Personally, I like beryl better (and its settings manager is awesome), and it can be installed from beryl-project.org's instructions with minimal invasiveness to Edgy.

---

### Post by Wolki on 2006-10-26
> **bruce89 said:**
> [http://cvs.gnome.org/viewcvs/metacity/src/compositor.c?view=markup](http://cvs.gnome.org/viewcvs/metacity/src/compositor.c?view=markup)

[http://mail.gnome.org/archives/desktop-devel-list/2006-October/msg00314.html](http://mail.gnome.org/archives/desktop-devel-list/2006-October/msg00314.html)

---

### Post by bruce89 on 2006-10-26
> **Wolki said:**
> [http://mail.gnome.org/archives/desktop-devel-list/2006-October/msg00314.html](http://mail.gnome.org/archives/desktop-devel-list/2006-October/msg00314.html)

I realise that Metacity's compositor wasn't going to have all the (useless) features of Compiz et al., but only the ones which would benefit usability.

---

### Post by Wolki on 2006-10-26
> **bruce89 said:**
> I realise that Metacity's compositor wasn't going to have all the (useless) features of Compiz et al., but only the ones which would benefit usability.

Yeah, that was exactly what I wanted too. Stuff that makes the desktop look nice and improves handling of stuff, but nothing that hinders usability and efficiency like compiz without severe tweaking.

The problem is, someone needs to actively develop it. And it seems like the metacity compositor's main developer quit, and noone else has volunteered yet.

---

### Post by matthias_k on 2006-10-27
Thanks for your feedback.

I had an SLED 10 release candidate installed on my desktop PC, it had XGL + Metacity pre-installed, you could enable it by a single switch. It worked out of the box with only very minor flaws (with my Radeon9800 that is).

Are you sure this is a metacity thing? I remember reading in the GNOME 2.16 release notes that Metacity is pretty much ready for 3D desktop eye candy, but then again, I'm no GNOME developer so I'm not sure of course.

---

### Post by MedivhX on 2006-10-27
One stupid question: Do beryl and compiz work better with XGL or AIGLX???

---

### Post by chaosgeisterchen on 2006-10-27
It's quite the same.. for everyday work, AIGLX works a lot better and Beryl runs evenly fast with it.

@AIGLX: Runs very nicely on my machine, finally.

---

### Post by Nonno Bassotto on 2006-10-27
What is more stable: Compiz from the repos or Beryl from Beryl-project? And which one is faster?

---

### Post by jdong on 2006-10-27
> **MedivhX said:**
> One stupid question: Do beryl and compiz work better with XGL or AIGLX???

If your card supports AIGLX, typically it's the way to go.... Xgl still has some minor issues, such as the inability to connect back to GDM for logout options.... Sometimes after locking the screen the CTRL key sticks, Shift+bksp zaps the X server unless you execute xmodmap, in which case you lose the ability to switch VT's... I can go on :)

---

### Post by TheRingmaster on 2006-10-27
is there a difference between xgl and aiglx?

---

### Post by raublekick on 2006-10-27
Will using Beryl + AIGLX work with the NV driver? The instructions on beryl-project don't say you have to install the nVidia driver, but it seems like it wouldn't work all that well without it.

---

### Post by jdong on 2006-10-27
No, the nv driver won't work with AIGLX because it does not support 3D rendering at all.

---

### Post by raublekick on 2006-10-27
> **jdong said:**
> No, the nv driver won't work with AIGLX because it does not support 3D rendering at all.

Figured as much, hopefully i can get the driver working in Edgy!

---

### Post by shining on 2006-10-27
> **PriceChild said:**
> 
Please remember though that ubuntu is meant to be scalable for a large base of hardware. Low-end machines just wouldn't function if this were default.


I thought the purpose of aiglx was to help the cpu by delaying stuff to the graphic card.
So I hope I totally misunderstood, because otherwise aiglx would be a miserable failure :)

---

### Post by MedivhX on 2006-10-27
So is nVidia GeForce4 MX440 enough for AIGLX + Beryl??? And should i install nVidia driver series 1.0-9*** or 1.0-8*** (because 1.0-9*** installs XGL)

---

### Post by PriceChild on 2006-10-27
> **shining said:**
> I thought the purpose of aiglx was to help the cpu by delaying stuff to the graphic card.
So I hope I totally misunderstood, because otherwise aiglx would be a miserable failure :)AIGLX is installed... and usable. It doesn't hamper performance at all for anyone not using it fully.> **MedivhX said:**
> So is nVidia GeForce4 MX440 enough for AIGLX + Beryl??? And should i install nVidia driver series 1.0-9*** or 1.0-8*** (because 1.0-9*** installs XGL)I advise you to use my guide with the beta 9xxx drivers and aiglx.

---

### Post by MedivhX on 2006-10-27
Is it in your sig??? The ''Beryl on Edgy'' one???

---

### Post by PriceChild on 2006-10-27
Yeah: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by MedivhX on 2006-10-27
Thanks!!! As soon as i get the new Edgy i will do so!!!

---

### Post by Spif on 2006-10-27
Edgy is the best distro ever. Have AIGLX and Beryl running flawlessly on my machine:)

---

### Post by MedivhX on 2006-10-27
This is offtopic but i noticed that many ppl have avatar with IceWeasel. Does that mean they hate Firefox???

---

### Post by TheRingmaster on 2006-10-27
> **MedivhX said:**
> This is offtopic but i noticed that many ppl have avatar with IceWeasel. Does that mean they hate Firefox???
no they just hate the foxes. lol

---

### Post by jdong on 2006-10-28
> **MedivhX said:**
> This is offtopic but i noticed that many ppl have avatar with IceWeasel. Does that mean they hate Firefox???
Naw, I think it's a fad right now to sport IceWeasel apparel because IceWeasel still sounds cool :)

---

### Post by chaosgeisterchen on 2006-10-28
Or because of the cool icon, but we better stop being offtopic.

@MedhivX: I have seen people running AIGLX/Beryl flawlessly with a GeForce 2 MX/400, does that answer your question?

---

### Post by jdong on 2006-10-28
> **chaosgeisterchen said:**
> Or because of the cool icon, but we better stop being offtopic.

@MedhivX: I have seen people running AIGLX/Beryl flawlessly with a GeForce 2 MX/400, does that answer your question?

I also run AIGLX/Beryl with a MX440.... Only issue is fullscreen 1280x1024 video playback sometimes is laggy with Beryl, in which case I just temporarily switch back to Metacity while doing movie watching. Other than that, desktop effects are very smooth.

---

### Post by Perfect Storm on 2006-10-28
I only turn it off for serious gaming stuff.
Sometimes it hardfreeze my computer if I exit a 3D game, so I switch to metacity when gaming.

---

