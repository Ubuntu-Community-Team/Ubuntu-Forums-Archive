---
title: "[SOLVED] Install emacs"
date: 2008-11-06
forum: Server Platforms
---

### Post by borpin on 2008-11-06
Hi,  I am trying to install emacs on 8.10 server with no success.  If I just type 'emacs' I am offered a variety of emacs packages to install. I am pretty sure I want emacs22-nox but if I
```
sudo aptitude install emacs22-nox
```
I get a 'package not found error.

Help I hate Vi!

---

### Post by meindian523 on 2008-11-06
Why not just ```
sudo aptitude install emacs
```?

---

### Post by borpin on 2008-11-06
Similar error in that is cannot find any packages containing 'emacs'

---

### Post by meindian523 on 2008-11-06
Check your repositories and make sure Universe is selected.Run ```
sudo apt-get update
``` and try again.

---

### Post by borpin on 2008-11-06
> **meindian523 said:**
> Check your repositories and make sure Universe is selected.Run ```
sudo apt-get update
``` and try again.

wheeeeeee :guitar:

Needed to do an update.

Many thanks (OK found out how!).  Brian

---

### Post by meindian523 on 2008-11-06
Please mark the thread as solved.

---

