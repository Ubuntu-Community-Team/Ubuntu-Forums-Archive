---
title: "Metacity can have Compiz style eye-candy now?"
date: 2006-10-20
forum: The Cafe
---

### Post by MetalMusicAddict on 2006-10-20
From [THIS]("http://www.gnome.org/start/2.16/notes/C/rnfrontpage.html") page.

"Metacity, GNOME's default window manager, makes its first steps into the world of 3D accelerated desktop computing. Many extensions to its compositor engine let your windows wobble, shrink, explode, fade in and out, bounce on window focus, and show other interesting, unusual or funny effects such as having different transparency for different window types like menus, dialogs, and main windows."

What are they pulling their code from Compiz or is it something they developed themselves? 

I just kinda stumbled across this. Trying to sort it out.

---

### Post by ComplexNumber on 2006-10-20
yup, that was one of the changes that was in gnome 2.16. quite old news really.

---

### Post by MetalMusicAddict on 2006-10-20
Has has Ubuntu compiled 2.16 with the options? I guess I should ask on IRC.

---

### Post by dabear on 2006-10-20
Developed themselves I think. It is not compiled by default, and you would need to use the flag --enable-compositor when building it. Alternatively, you can download the spiftacity package and run
```
 spiftacity --replace&;sleep 30;metacity --replace&

```
But before you need to enable the composite key in gconf - do a search for "composit" with ctrl +f and all options ticked off - I can't remember the exact location right now, as I am not on my ubuntu box.

Be warned though, windows will have fading ability, but the whole screen will be white and not usable, that's why I put the sleep part there, so you could try it for 30, before metacity takes over again.

It is still pretty alphaish, and **is not at all reccomended** for general use (spiftacity is the development version of metacity).

To use this, you would have to have support for glx_texture_from_pixmap-extension, meaning one of the following cards: Radeon 7000-9250 with ('ati' driver), Intel Integrated ('i810' driver) or the newest nvidia drivers.

Alternatively, you can use XGL, which provides this extension too.

Obviously, edgy (or rather the latest gtk) is required.

Also, hopefully all bugs will be sorted out in time for Gnome 2.18, and we will have composite enabled by default in Feisty Fawn.

---

### Post by Wolki on 2006-10-20
spiftacity is actually the compositing-enabled version of metacity 2.13 something, i.e., the development version of last release. The new one doesn't seem to work either, if reports from people who have tried it on bugzilla can be believed. :-/

Personally I don't have much hope for next version either... which sucks as I'd like to have some compostiting fastness, and compiz is nowhere near usable enough :-/

---

### Post by weatherman on 2006-10-20
they're pretty much going to have the same stuff kde has had for ages. Nothing too exciting really.

---

### Post by chaosgeisterchen on 2006-10-20
So KDE has compiz-style-eyecandy?

I'm waiting for Beryl to replace KWin/Metacity for me...

---

### Post by ComplexNumber on 2006-10-20
> **weatherman said:**
> they're pretty much going to have the same stuff kde has had for ages. Nothing too exciting really.
yes, but its only useless  eye candy, so its not surprising kde had it first.

---

### Post by chaosgeisterchen on 2006-10-20
I plead you not to come up with KDE-Gnome issues here..

---

### Post by GeneralZod on 2006-10-20
> **chaosgeisterchen said:**
> So KDE has compiz-style-eyecandy?

Nope - although Lubos just started working on it [last Tuesday](http://www.kdedevelopers.org/node/2441).  He has to learn OpenGL first, though :)

---

### Post by chaosgeisterchen on 2006-10-20
This will be part of KDE4. I hope they implement a good plugin-interface to assure good integration into Beryl, which will be still the leader concerning this genre.

Extensible KWin4. Sounds good so far. I could suggest that to the KDE guys :)

---

