---
title: "The purpose behind *dev packages"
date: 2004-11-17
forum: The Cafe
---

### Post by tfwo on 2004-11-17
Hmm, I wonder, what's the purpose of having -dev packages in deb and rpm based distros? It's sometimes quite annoying when you start compiling something and realise that you just didn't install some corresponding dev-packages... In slackware and gentoo a package always comes "complete" with all development files, documentation, etc. So, what do you think are the pros for having -dev packages?

---

### Post by dataw0lf on 2004-11-17
The *dev packages are usually orientated toward developers.  With apt, it automagickally (most of the time) resolves conflicts by installing libraries you need.  Not everyone compiles their applications.
dataw0lf

---

### Post by daniels on 2004-11-17
If you were to install a base system with, say, X, GNOME, GTK, Evolution, et al, for someone, then that's not going to be that big.  If you include all the development stuff as well, it will be massive.  It's just unnecessary.

---

### Post by az on 2004-11-17
That is what is meant by binary packages.  Just the binaries, no headers or source.

Using the headers, you can compile agains the binaries without the source...

---

