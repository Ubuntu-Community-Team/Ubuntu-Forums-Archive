---
title: "Xmir rejected by mir"
date: 2015-10-06
forum: Ubuntu Phone and Tablet
---

### Post by qduaty on 2015-10-06
Can anyone tell me, how to correctly invoke Xmir on Ubuntu Phone so that it's not rejected on mir socket connection?

I installed the current version 24 of 'ubuntu' image (so called "community custom") on my bq e4.5, with writable image. In my attempts to launch Xmir, I tried all three mir sockets I found, launching with sudo, and confirmed the problem with mir-examples or mir-tests, whatever - they don't connect as well. There are no entries about rejection in unity8.log. I even tried Xorg - quits without error with mir driver (fbdev works, invisible). Of course, I also queried google with many combinations of words, with no success.

Edit. **Xmir works on bq-aquaris system image**.

---

### Post by pixelro on 2015-10-07
maybe try on IRC? #ubuntu-mir (freenode)

i think you need a .desktop file. something like this "Xmir :0 --desktop_file_hint=whatever_app"

there is 0 documentation, so your best change is 1. read the source code on launchpad or 2 ask developers on IRC

also try Xmir --help

---

### Post by qduaty on 2015-10-14
> **pixelro said:**
> i think you need a .desktop file. something like this "Xmir :0 --desktop_file_hint=whatever_app"Xmir has no such option.

---

### Post by krusty8 on 2015-11-15
> **qduaty said:**
> Xmir has no such option.

It somehow does [https://www.youtube.com/watch?v=XfMLzlki9XE&t=85](https://www.youtube.com/watch?v=XfMLzlki9XE&t=85) also ```
strings /usr/bin/Xmir | grep desktop_file_hint
``` even though it doesn't  show up in ```
Xmir -h
``` and I have no clue what it does. It seems to work fine without it.

---

