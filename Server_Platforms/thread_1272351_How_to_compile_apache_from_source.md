---
title: "How to compile apache from source"
date: 2009-09-22
forum: Server Platforms
---

### Post by floatingworld on 2009-09-22
I need to use a custom Apache module from a software vendor (mod_caucho for Resin / Quercus - PHP in Java and vice versa, cool stuff).  Apparently I need to compile the module myself, and additionally re-compile Apache using the --with-apxs option.

I've only compiled from source a few times and the instructions I'm finding for doing Apache on Ubuntu involve downloading directly from the apache.org web site and compiling a separate version that doesn't use the Ubuntu file locations or things like the a2ensite/a2dissite scripts.

But I like the Ubuntu cfg of Apache and I'd want to keep it.  I've gotten the impression that there's usually a way to fetch the source code of an app through aptitude and carry on with compiling from there, but could someone sketch out the basic steps to use in my case?

Thanks in advance, fw

---

### Post by Lars Noodén on 2009-09-22
Uncomment the deb-src lines in /etc/apt/sources.list and update.
Then you'll need to add the build prerequisites, and so on.

These will point you in the right direction, but you may want to find other HowTos and tutorials.

[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

[http://www.debian.org/doc/debian-policy/ap-pkg-sourcepkg.html](http://www.debian.org/doc/debian-policy/ap-pkg-sourcepkg.html)

---

