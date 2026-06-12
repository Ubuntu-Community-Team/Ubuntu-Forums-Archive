---
title: "DustbunnyOS advice?"
date: 2009-02-12
forum: The Cafe
---

### Post by Kopachris on 2009-02-12
I've been working on making a Linux distro for about a year now.  Most of my time has been spent doing research.  There are a few ways of going about doing this.  Simply customizing Ubuntu and making a LiveCD out of it seemed too messy* and amateur-ish to me.  Building LFS is more complicated than it needs to be.  I think this is the process I've decided upon:


[LIST=1]
[*] Combine LiveCD creation instructions with LFS instructions to copy Ubuntu's base over to a new partition and make it bootable.
[*] Read through BLFS (already read through LFS) to get an overview of what needs to happen.
[*] Install dpkg, aptitude, apt-get.
[*] Follow instructions at [http://www.x.org/wiki/ModularDevelopersGuide](http://www.x.org/wiki/ModularDevelopersGuide) to compile xorg.
[*] Follow instructions at [http://www.iaeste.or.at/doc/gnome-faq/html/compilinggnome.html](http://www.iaeste.or.at/doc/gnome-faq/html/compilinggnome.html) to compile GNOME, but first read the entire faq at [http://www.iaeste.or.at/doc/gnome-faq/html/index.html](http://www.iaeste.or.at/doc/gnome-faq/html/index.html).
[*] Install everything else.
[/LIST]
 
After that, of course, we'd make an icon set, a GTK theme (probably a recoloration of Human), and a sound theme.  Once everything is said and done, I'd make some installation scripts and a friend will make a Python frontend for them (something similar to Ubiquity) and make a LiveCD.  I'll simply take the kernel configuration from Ubuntu for at least the first release.  I'll be reading some more on compiling the kernel (I always seem to do it wrong, even though it throws no errors...), then I'll compile a kernel for DustbunnyOS.

So, what do you think?  Is the idea sound?  Any comments or advice would be appreciated.

*I hate all those "ubuntu" package version numbers (like 2.3.99.6-2ubuntu4).

---

