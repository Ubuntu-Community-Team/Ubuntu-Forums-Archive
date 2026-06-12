---
title: "display problems after latest updates"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kurja on 2012-03-30
When I minimize a window and then restore it from the launcher, the window is all white. If I drag it around a bit, the content reappears. Is anyone experiencing this?

Another weirdness is that when the computer wakes from suspend, the launcher area is messed up (like some chroma noise pattern). It gets back to normal when I move the mouse to the left to bring out the launcher.

Is anyone else experiencing these things?

---

### Post by kurja on 2012-03-31
I'm still getting this behaviour, and it's very repeatable. Aren't any of you seeing this happen?

---

### Post by exploder on 2012-03-31
I can confirm this behaviour. If I minimize Firefox and restore it the screen is white.

---

### Post by kancerman on 2012-03-31
I get something similar & repetitious under unity -&- unity-2d ... but mine is tabs in Chrome Unstable from Google themselves go black -&- columnized or tabbed text & icons disappear/reappear with mouseover or mousewipe

---

### Post by madjr on 2012-03-31
please report bug and grab some screenshots.

from terminal:

**ubuntu-bug unity**

---

### Post by kurja on 2012-03-31
I'm trying right now, never done it before so we'll see ;)

For the record I'm getting it with other apps/windows as well, not just with firefox.

---

### Post by kurja on 2012-03-31
Okay, I ran ```
**ubuntu-bug unity**
```and got directed to launchpad web site - where I got totally lost with creating an account and so on. Bug reporting program said that a bug has been reported, but I don't recall typing in a description of any kind.

Me dumb.

Maybe try again.

---

### Post by kurja on 2012-03-31
(looks like) a success. [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/970140](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/970140)

---

### Post by palimmo on 2012-04-04
Same problem.

---

### Post by xyzzyman on 2012-04-09
Happening here, usually with totem and virtualbox... Added to both bugs, including the main confirmed one:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658)

---

### Post by kurja on 2012-04-12
appears to have been fixed!!!

---

