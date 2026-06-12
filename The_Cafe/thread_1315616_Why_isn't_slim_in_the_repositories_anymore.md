---
title: "Why isn't slim in the repositories anymore?"
date: 2009-11-05
forum: The Cafe
---

### Post by Warpnow on 2009-11-05
Really annoying...I used it on most of my systems.

---

### Post by Tibuda on 2009-11-05
Yeah, me too. This explains it: [http://osdir.com/ml/ubuntu-devel-discuss/2009-09/msg00097.html](http://osdir.com/ml/ubuntu-devel-discuss/2009-09/msg00097.html)

> The reason it is not in karmic (and can't be now) is presumably because it was not in Debian when we synced from Debian earlier in the release cycle. Ubuntu has not modified it in any way - we've just taken it from Debian. If it gets back in Debian it will get back in Ubuntu.

Looking at packages.debian.org I find slim in lenny and sid. It has some terrible bugs though including one that says you can login as root without a password! It sounds like it is good that it is not in karmic!

---

### Post by Warpnow on 2009-11-05
So...slim is not included...GDM is now entirely gnome dependent with a broken legacy package...what are we supposed to use to login?

---

### Post by Tibuda on 2009-11-05
Yeah, that sucks. Some login managers:
[http://packages.ubuntu.com/karmic/xdm](http://packages.ubuntu.com/karmic/xdm)
[http://packages.ubuntu.com/karmic/sdm](http://packages.ubuntu.com/karmic/sdm)
[http://packages.ubuntu.com/karmic/wdm](http://packages.ubuntu.com/karmic/wdm)
[http://packages.ubuntu.com/karmic/ldm](http://packages.ubuntu.com/karmic/ldm)
[http://packages.ubuntu.com/karmic/kdm](http://packages.ubuntu.com/karmic/kdm)

You could also try to install the jaunty package for slim, but I'm not sure if it would work:
[http://packages.ubuntu.com/jaunty/slim](http://packages.ubuntu.com/jaunty/slim)

---

### Post by kavon89 on 2009-11-05
Best bet is to just install it from source. The version Debian repos have might not be the very latest and some of those severe bugs may have been resolved.

---

### Post by liquidbee on 2009-11-05
Download, compile, use .. share!

---

