---
title: "GTK = GIMP Tool Kit?"
date: 2007-09-22
forum: The Cafe
---

### Post by Nekiruhs on 2007-09-22
Hmm. Ok. Will some one explain this to me? 
As I understand it, GTK = GIMP Toolkit. How do we get a whole graphics tool kit, which GIMP is written in by the way, out of the GNU Image Manipulation Program? Basically how did GIMP get a toolkit named after it?

---

### Post by bruce89 on 2007-09-22
> **Nekiruhs said:**
> Hmm. Ok. Will some one explain this to me? 
As I understand it, GTK = GIMP Toolkit. How do we get a whole graphics tool kit, which GIMP is written in by the way, out of the GNU Image Manipulation Program? Basically how did GIMP get a toolkit named after it?

Because the GIMP developers created it so they didn't have to use the non-free Motif or QT.

Anyway, GTK+ has a "+" on the end, unless you're referring to a very early version (< 1.0).

---

### Post by mostwanted on 2007-09-22
GIMP used to use a proprietary toolkit, but then the developers were unsatisfied with that situation and also unsatisfied with the number of good open multi-platform toolkits (Qt was closed-source on Windows back then), so they decided to make their own and use that. This is straight from memory, so I might be slightly off, gonna go check on Wikipedia right now (which you should have done too, you lazy chump :) ).

---

### Post by FuturePilot on 2007-09-22
The developers of Gimp are responsible for also developing GTK. Or something like that. So if Gimp was never developed GTK or Gnome for that matter perhaps would not exist. I'm not 100% sure about that though, someone correct me if I'm wrong.

---

### Post by bruce89 on 2007-09-22
> **mostwanted said:**
> (Qt was closed-source on Windows back then)

QT was under the QPL on all platforms, which was deemed non-free by the FSF.

The GNU project were pissed off that KDE was using non-free software, so they started GNOME, who chose GTK+

It is now under the GPL for people using it for GPL stuff, if you want to make non-free software with QT, you need a licence.

GTK+ is under the LGPL, so it can be used for free and non-free software without royalties.

---

### Post by samjh on 2007-09-22
Before Gnome, the only major desktop GUI for Linux was KDE.  KDE was written using Qt, a then-proprietary library (now it is GPL'ed).  The founders of the Gnome project did not like that a dominant Linux desktop GUI was written using a proprietary library, so they set about creating an alternative, and named it GNOME.

The problem was... they had no alternative GUI widget set available which could offer nearly as much power as Qt among FOSS projects available at the time.  So they picked GIMP, which used a relatively rich widget set, modified it so it was even richer, and named the widget library GTK.  Thus GTK became the widget set for GNOME, and GIMP became its development testbed and showcase for the widget set.

---

### Post by bobbocanfly on 2007-09-22
Wow didnt know all this. I was always under the impressiong GTK stood fro Gnome Toolkit and was developed by Gnome dev's specifically for the Gnome project

---

### Post by az on 2007-09-22
> **bobbocanfly said:**
> Wow didnt know all this. I was always under the impressiong GTK stood fro Gnome Toolkit and was developed by Gnome dev's specifically for the Gnome project

XFCE is a completely separate (competing) desktop environment and it uses GTK+, too.

---

### Post by newbie2 on 2007-09-23
> **bobbocanfly said:**
> Wow didnt know all this. I was always under the impressiong GTK stood fro Gnome Toolkit and was developed by Gnome dev's specifically for the Gnome project
[http://www.acronymfinder.com/af-query.asp?Acronym=gtk&Find=find&string=exact](http://www.acronymfinder.com/af-query.asp?Acronym=gtk&Find=find&string=exact)
;)

---

