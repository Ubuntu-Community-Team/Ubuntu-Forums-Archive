---
title: "PHP 5.3.3 on Lucid"
date: 2010-10-16
forum: Server Platforms
---

### Post by 448191 on 2010-10-16
PHP 5.3.3 seems to be in Maverick.

What would be the "best" (as in, least maintenance in the future) way to update to that without updating to 10.10. The past few years I've been updating to the latest release as soon as it came available, but I'm trying to get a more stable working environment; yet another force to compete with my urge to get the latest innovations of everything ;)

I know I can compile, and even run a second PHP server alongside my current one. But basically I'm looking for a solution that requires minimal maintenance. This is my work and nobody likes work getting boring and/or cumbersome. I prefer not to compile, get in a shitload of dependencies or otherwise get myself into a whole lot work I don't really have the time for.

Admittedly I don't have high hopes for any magic solutions, but here I am, trying regardless. Magicians this way please.

---

### Post by lykwydchykyn on 2010-10-16
I typically use the apt-src method of backporting, it works pretty well most of the time.  Basically it works like this:
 - Install apt-src
 - Add a **source repository** (not binary) for the newer version of Ubuntu to your sources.list.  E.g.:
```

deb-src http://us.archive.ubuntu.com/ubuntu main universe

```

 - Now execute:
```

apt-src update
apt-src install somepackage && apt-src -i build somepackage

```

If all goes well, that will download the source and build dependencies of the package from Maverick and compile it for Lucid.  It also installs it as a package  and does all the little niceties you get from a normal repository install (man pages, binaries under /usr instead of /usr/local, etc).

Possible snags might be if you can't install the build dependencies (if it requires a newer version than is available in Lucid), or if it just fails to compile for some reason.  But in most cases this approach works fine.

---

### Post by 448191 on 2010-10-17
This seems helpful, thanks.

---

