---
title: "Contributed beagle 0.0.12"
date: 2005-07-25
forum: Ubuntu Backports
---

### Post by davidsf on 2005-07-25
Hi,

I have backported beagle 0.0.12 from breezy (and libgmime2.1-2.1.15 that beagle needs).

[http://www.gnome.org/~davidsf/ubuntu/hoary/mono/](http://www.gnome.org/~davidsf/ubuntu/hoary/mono/)

Cheers

---

### Post by jdong on 2005-07-25
That's cool :). I'm sure many will appreciate this.

Unfortunately, since this new beagle needs new libraries, I won't be able to put this in the official Backports repository.

---

### Post by Confuse on 2005-07-25
Ok, got it working after battling with dependencies. So far so good, the app works!

---

### Post by davidsf on 2005-07-26
[QUOTE=jdong]
Unfortunately, since this new beagle needs new libraries, I won't be able to put this in the official Backports repository.[/QUOTE]

Well, the new library that beagle needs it's new version of libgmime2.1 (that's in backports already for beagle 0.0.11). I think all the dependecies are in my url.

Never mind, it's ok if you think that this packages can't be in official backports.

Cheers

---

### Post by manicka on 2005-07-26
[QUOTE=davidsf]Well, the new library that beagle needs it's new version of libgmime2.1 (that's in backports already for beagle 0.0.11). I think all the dependecies are in my url.

Never mind, it's ok if you think that this packages can't be in official backports.

Cheers[/QUOTE]
 The mono updates and associated files that are at our url break the version of tomboy that I have installed and beagle wouldn't even start. 
I'm back with beagle 0.0.11.1 and mono 1.1.7

---

