---
title: "Restricted extras vs Medibuntu"
date: 2009-12-12
forum: The Cafe
---

### Post by armandh on 2009-12-12
Medibuntu is about my only use of the command line
so I thought I would try the restricted extras instead
installed easily but my test dvd did not play
de installed easily too.

Medibuntu's stuff was cut and pasted to the command line and just worked. 
the test dvd just played.
in this case I will stick with the successful harder way.

The results....
I finally upgraded the family room media player
I had used an old 933 P-III with a DVI out video card
now a tiny atom/ion itx box & brick power-supply 
it even looks like an AV thing
rather than an old computer.

---

### Post by coffeecat on 2009-12-12
> **armandh said:**
> I thought I would try the restricted extras instead
installed easily but my test dvd did not play
de installed easily too.

This is not a question of ubuntu-restricted-extras versus Medibuntu. For encrypted DVD playback the two are complementary.

With ubuntu-restricted-extras you would have installed the libdvdread4 library. From the libdvdread4 package description:

> libdvdread provides the functionality that is required to access many DVDs. It
parses IFO files, reads NAV-blocks, and performs CSS authentication and
descrambling.

libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
If found, libdvdcss will be used to decrypt sections of the DVD as necessary..

Note that it says, "**if found**, libdvdcss will be used..." The library libdvdcss2 is provided by Medibuntu and without it you will not be able to play encrypted DVDs. In fact, without libdvdread4 you won't be able to play them either. The reason that you could after you "de installed" ubuntu-restricted-extras is that restricted-extras is merely a meta-package. All its dependencies, including libdvdread4, will remain installed even if ubuntu-restricted-extras has been uninstalled.

---

### Post by armandh on 2009-12-12
well if I have to go to medibuntu anyway...

OK. what does medibuntu not have?
I still need flash

I find VLC and medibuntu completes the AV playback
but I could be missing some thing

---

### Post by Ginsu543 on 2009-12-12
I think it's more of a both/and rather than either/or, since they both add functionality to Ubuntu. Besides AV-related files, ubuntu-restricted-extras also installs Microsoft TrueType fonts, flash, java, and cabextractor. I always install both on my Ubuntu systems, even on my Dell Vostro A90 with a 4 GB SSD (there's enough room for both).

---

### Post by murderslastcrow on 2009-12-12
I've never used Medibuntu. What does it have to offer?

---

### Post by murderslastcrow on 2009-12-12
Just checked the official site. Doesn't seem too compelling to me, although it certainly did have its place in the olden days.

---

### Post by SuperSonic4 on 2009-12-12
essentially non-free codecs and other non-free software useful to ubuntu user

---

### Post by NormanFLinux on 2009-12-12
Medibuntu offers proprietary software and third party codecs for media playback that cannot be shipped with Ubuntu for legal reasons. Ubuntu only offers free software and the minimum proprietary hardware drivers needed to make your computer run. Nothing else. That's why adding it to your Software Sources list will give you a full multimedia desktop.

---

### Post by drawkcab on 2009-12-12
> **Ginsu543 said:**
> I think it's more of a both/and rather than either/or, since they both add functionality to Ubuntu. Besides AV-related files, ubuntu-restricted-extras also installs Microsoft TrueType fonts, flash, java, and cabextractor. I always install both on my Ubuntu systems, even on my Dell Vostro A90 with a 4 GB SSD (there's enough room for both).

agreed

---

