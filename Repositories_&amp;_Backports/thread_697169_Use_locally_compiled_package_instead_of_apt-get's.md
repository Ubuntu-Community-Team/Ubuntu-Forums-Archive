---
title: "Use locally compiled package instead of apt-get's"
date: 2008-02-14
forum: Repositories &amp; Backports
---

### Post by Ambush Commander on 2008-02-14
As a developer, I occasionally compile versions of software for my own use. However, I'm also your Average Joe end-user, so there are some packages of software that I have no intention of ever compiling myself, and would prefer Synaptic/apt-get handle for me. How can these two systems co-exists?

For example, I recently compiled my own version of libxml. Since make install was successful, I figured that I ought to remove it from the package manager. However, if I were to do that, I'd break the dependencies for dozens of other packages.

What should I do?

---

### Post by talowe on 2008-02-16
See this link [https://wiki.ubuntu.com/PbuilderHowto]("https://wiki.ubuntu.com/PbuilderHowto") to use pbuilder to build your own package and set-up a local repository.  Then you can add your local repo to sources.list and install and remove your packages with apt.

This link [http://wiki.gnucash.org/wiki/Debian]("http://wiki.gnucash.org/wiki/Debian")  might be useful for seeing howto edit debian/rules and whatnot for customizing your build.

especially the ```
debchange -nmu
``` command, which will increment the package version, so your deb has a slightly higher version and will be chosen over the ubuntu-packaged version.

---

