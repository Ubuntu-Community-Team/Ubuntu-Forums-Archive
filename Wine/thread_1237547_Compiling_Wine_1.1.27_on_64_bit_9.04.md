---
title: "Compiling Wine 1.1.27 on 64 bit 9.04"
date: 2009-08-11
forum: Wine
---

### Post by dardack on 2009-08-11
I posted to wine mailing list, no help yet:

I'm trying to compile 1.1.27, and I run ./configure and  get

configure: WARNING: libgsm 32-bit development files not found, gsm 06.10 codec won't be supported.

So trying to figure out how to install those on 64 bit unbuntu.

Anyone know?

---

### Post by bruno9779 on 2009-09-13
I am having the same problem. on Jaunty

I will post if i get to the end of this

---

### Post by beastrace91 on 2009-09-13
Try installing the "ia32-libs-tools" package via terminal or Synaptic (also make sure you have "ia32-libs" installed as well).

And in case you haven't already use apt's build-dep command to grab any other dependencies you might need. ```
sudo apt-get build-dep wine
```

Hope this helps some,
~Jeff

---

### Post by YokoZar on 2009-09-14
There is no 32 bit libgsm available on Jaunty 64; builds will be stuck without it.  [http://ubuntuforums.org/showthread.php?p=7829848#post7829848](http://ubuntuforums.org/showthread.php?p=7829848#post7829848)

> **YokoZar said:**
> I've uploaded my 1.1.28 packages for Ubuntu (9.04 is already built, 8.10
and 8.04 are still building as I write this).  One of the fixes in this
package is to build with support for libgsm, a new feature in Wine that
allows Ventrilo support out of the box.

However, this will only work on 32-bit Ubuntu at this time, as there is
no 32 bit version of this library available on Ubuntu 64.  I've already
fixed this in the development version (Ubuntu 9.10) and the "wine1.2"
package there.

As far as I know the only application affected is Ventrilo.  So just to
conclude:

Ubuntu 8.04, 8.10, 9.04 32 bit with Wine 1.1.28 or higher: Vent works.
Ubuntu 8.04, 8.10, 9.04 64 bit: Vent doesn't work.
Ubuntu 9.10 with wine1.2 package: Vent works.

Note that the "wine1.2" package is just the current Wine beta:
[http://yokozar.org/blog/archives/103](http://yokozar.org/blog/archives/103)

---

### Post by bruno9779 on 2009-09-17
Just for the record, Wine 32bit works flawless also without libgsm.
It is used for some mobile phone function, so it does not affect my normal use of wine

---

### Post by dardack on 2009-10-11
> **YokoZar said:**
> There is no 32 bit libgsm available on Jaunty 64; builds will be stuck without it.  [http://ubuntuforums.org/showthread.php?p=7829848#post7829848](http://ubuntuforums.org/showthread.php?p=7829848#post7829848)

YokoZar, i see you say you fixed for 9.10, which I will probably go to when it's official released.  I edit mouse.c in wine for some customization with WoW, so I manually compile wine.  Will I be able to get this libgsm 32 bit for 64bit 9.10?  Also, configure: libmpg123 32-bit development files not found (or too old), mp3 codec won't be supported.
configure: libopenal 32-bit development files not found (or too old), OpenAL won't be supported.  Will these 2 be supported also in 64 bit 9.10?

---

