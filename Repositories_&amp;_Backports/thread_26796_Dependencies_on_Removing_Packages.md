---
title: "Dependencies on Removing Packages"
date: 2005-04-13
forum: Repositories &amp; Backports
---

### Post by dbolgheroni on 2005-04-13
Hi,

I'm trying to remove some packages in a different way.

The portable NetBSD package system (runs on GNU/Linux too) has useful
options regarding this, like -r and -R in pkg_delete. I don't know if apt uses one of these options by default, removing only the package specified.

I would like to remove the given package and any packages it depends on,
unless some other package still needs a dependent package.

Are there any way to do this with apt?

pkg_delete manpage can be found at:

[http://netbsd.gw.com/cgi-bin/man-cgi?pkg_delete++NetBSD-current](http://netbsd.gw.com/cgi-bin/man-cgi?pkg_delete++NetBSD-current)

Thank you.

---

### Post by XDevHald on 2005-04-13
To get certain packages removed by name type as root:

**apt-get remove "package name"**

and to remove files that the package installed along with it would be:

**apt-get --purge remove "package name"**

---

### Post by dbolgheroni on 2005-04-14
Oh, apt-get does this by default. I didn't see it before.

I think this is essencial and do not accumulate a lot of packages in your system if you don't want. yum doesn't do this even if you know what you're doing (e.g. with a parameter to yum), and this is very bad in my opinion.

Thank you.

---

### Post by mendicant on 2005-04-14
You also probably want to use aptitude instead of apt-get, to manage the automatically installed things.  See item 2:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

This does more of what you want, I think, but also requires that you use aptitude to install packages (you can manually go in and label automatically installed stuff like the whole libraries section, if needed).  I'm not sure if synaptic also does this, as I don't use it.

---

