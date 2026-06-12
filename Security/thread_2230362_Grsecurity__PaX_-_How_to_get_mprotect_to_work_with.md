---
title: "Grsecurity / PaX - How to get mprotect to work with Kubuntu?"
date: 2014-06-18
forum: Security
---

### Post by Remten on 2014-06-18
I'm able to run Kubuntu with a Grsecurity patch so long as I don't turn mprotect on.
But once mprotect is on, I can't get a login screen.

Any suggestions for which binaries to individually exclude from mprotect (via paxctl) in order to get the login screen to work?

---

### Post by sandyd on 2014-06-18
Try excluding X and kdm (/usr/bin/X and /usr/bin/kdm)

---

### Post by Remten on 2014-06-18
I disabled it on Xorg -- didn't help.

Trying with /usr/bin/kdm gives a "No such file or directory" error.

---

