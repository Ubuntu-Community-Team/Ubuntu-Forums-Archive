---
title: "[OT] Lol, Portage on Ubuntu"
date: 2005-02-10
forum: The Cafe
---

### Post by jdong on 2005-02-10
Following a HOWTO on Gentoo forums, I was able to unpack Portage onto Ubuntu Hoary. Some quick hacks to emerge (i.e. dpkg-query checks during dependencies), and I managed to emerge mjpegtools.

Just a fun proof-of-concept.... LOL.

IMO, it's a bit dangerous to post the source for this hack. If I can stabilize it, I just may post it.  :?

---

### Post by Titeuf on 2005-02-10
This would make an awesome combo:
the simplicity and It Just Works of ubuntu combined with portage
I moved from Gentoo to Ubuntu, but I still miss portage :(

---

### Post by Randabis on 2005-02-10
Wow, that's awesome. I'm dual booting both right now. :)

---

### Post by kassetra on 2005-02-10
Wouldn't that be the best of all linux worlds possible here?  Portage, Ubuntu, apt... wow.  

I just can't even imagine that kind of possibility.

---

### Post by TravisNewman on 2005-02-10
There is something similar to portage for apt. apt-build, I think. It's definitely not the same, but it still resolves dependenies and compiles.

---

### Post by az on 2005-02-11
apt-get build-dep $package
apt-get -b source %package

---

### Post by Titeuf on 2005-02-11
[QUOTE=panickedthumb]There is something similar to portage for apt. apt-build, I think. It's definitely not the same, but it still resolves dependenies and compiles.[/QUOTE]
 This is just the worst part of portage IMHO: that it compiles everything, it takes way too much time.
I love portage because of the USE-flags and also that almost everything is in it: mplayer, win32codecs, ...

---

### Post by jdong on 2005-02-11
I want to port portage primarily for its abundance of apps, and its ease-of-development.

I want a good native way to deal with w32codecs, etc.

---

### Post by Dylanby on 2005-02-11
You could try [pkgsrc](http://www.pkgsrc.org/) 

I've read posts from people who've used it on Slack. It'd be interesting to see how it compares to dpkg/apt.

---

### Post by Titeuf on 2005-02-13
Can you post a small howto on how to do this ?
I would love to experiment with this :)

---

### Post by rufius on 2005-02-13
[QUOTE=jdong]Following a HOWTO on Gentoo forums, I was able to unpack Portage onto Ubuntu Hoary. Some quick hacks to emerge (i.e. dpkg-query checks during dependencies), and I managed to emerge mjpegtools.

Just a fun proof-of-concept.... LOL.

IMO, it's a bit dangerous to post the source for this hack. If I can stabilize it, I just may post it.  :?[/QUOTE]
 lol Yikes John thats scary to me. Portage is ok but I think I'll stick to the deb's. :)

---

