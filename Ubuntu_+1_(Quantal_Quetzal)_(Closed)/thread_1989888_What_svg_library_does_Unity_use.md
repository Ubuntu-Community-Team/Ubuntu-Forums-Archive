---
title: "What svg library does Unity use?"
date: 2012-05-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Finalfantasykid on 2012-05-28
I want to file a bug report, but I believe that the bug should go to the svg library that Unity uses, but I do not know what it is.  I think it also affects the gnome image viewer.

---

### Post by ScislaC on 2012-05-29
I'm pretty sure Eye Of Gnome uses librsvg, I can't speak for unity though.

Just curious, what's the issue?

---

### Post by Gyokuro on 2012-05-29
Have you already looked which libs are necessary to compile unity? Below mentioned file lists all:

[http://bazaar.launchpad.net/~unity-team/unity/trunk/view/head:/INSTALL](http://bazaar.launchpad.net/~unity-team/unity/trunk/view/head:/INSTALL)

---

### Post by Finalfantasykid on 2012-05-29
^Thanks, based on that list, it looks like librsvg is the culprit.  I've filed a bug for it upstream :)

---

