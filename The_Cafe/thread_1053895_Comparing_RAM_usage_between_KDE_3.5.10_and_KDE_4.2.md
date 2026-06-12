---
title: "Comparing RAM usage between KDE 3.5.10 and KDE 4.2"
date: 2009-01-29
forum: The Cafe
---

### Post by Hallvor on 2009-01-29
I was thinking of testing the differences in RAM usage between KDE 4.2 and KDE 3.5.10 in Opensuse. Is it possible to do a fair comparison between the two from livecds, or is it necessary to install both of them to the hard drive? I would rather do the testing from livecds if the output is reliable.

---

### Post by Sand &amp; Mercury on 2009-01-29
Testing from LiveCDs should be ok I think, but remember that SUSE's implementation of KDE (both 3.5 and 4.2) is not a plain vanilla one, so any modifications they've made to it themselves may offset your data a little bit.

---

### Post by GeneralZod on 2009-01-29
Ideally, you'd compile both yourself based on the same distro, but this will probably work OK.  Do make sure you know what you're doing, though, as measuring memory usage is more complex than most people think: see here for a good analysis:

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)

I'd be particularly interested in the xserver usage, as I suspect 4.x is considerably more pixmap-hungry than 3.x due to Qt4's double-buffering.  xrestop is an additional handy tool, here, if you want to see which programs are the most pixmap hungry.

---

