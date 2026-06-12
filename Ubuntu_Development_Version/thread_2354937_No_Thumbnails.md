---
title: "No Thumbnails"
date: 2017-03-07
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-03-07
Hi All,

There doesn't seems to be any thumbnails with 17.04 (confirmed with another person, who is actually the one that brought it up). Does anyone know why?

There is [this older thread]("https://ubuntuforums.org/showthread.php?t=2291524&highlight=thumbnails"), but things seem to be o.k. on my 16.10 test computer. Also, I tried the suggestion from [this post]("https://ubuntuforums.org/showthread.php?t=2291524&p=13345070#post13345070"), and still no thumbnails.

Oh, I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602"). I'll add myself as "affected by" there.

---

### Post by harry332 on 2017-03-08
True, certain thumbnails (like jpeg and png) are gone.
I think this bug report is the correct one (the one Doug S found):
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602)

However, some thumbnails do appear to be generated: tiff and pdf.

This bug is persistant with nautilus versions 3.20 and 3.22 and 3.23.90 too.
So this may not be a nautilus bug.

---

### Post by howefield on 2017-03-08
.jpgs used as a desktop wallpaper subsequently generate thumbnails. Not a workaround, just an observation :)

---

### Post by Doug S on 2017-03-23
Solved with updates of today.

---

