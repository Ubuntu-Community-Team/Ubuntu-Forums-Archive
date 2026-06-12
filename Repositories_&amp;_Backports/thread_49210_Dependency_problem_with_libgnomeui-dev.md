---
title: "Dependency problem with libgnomeui-dev"
date: 2005-07-15
forum: Repositories &amp; Backports
---

### Post by zeroK on 2005-07-15
I'm currently trying to install libgnomeui-dev (to be able to compile evince) but I have some problems with its dependencies :(

> The following packages have unmet dependencies:
  libgnomeui-dev: Depends: libgnome2-dev (>= 2.6.0) but it is not going to be installed
                  Depends: libbonoboui2-dev (>= 2.5.4) but it is not going to be installed
                  Depends: libgnomevfs2-dev (>= 2.7.1) but it is not going to be installed
E: Broken packages

This seems to be  (at least partially) caused by libgnutls11-dev depending on a non-existing libgnutls11 version.

Has anyone already come up with a solution for this? Otherwise I'd think that this is worth a bug report since it's blocking nearly all gnome*-dev packages here.

---

### Post by varunus on 2005-07-15
I know this doesn't answer your question, but isn't evince in universe?  Or are you trying to compile a newer version?

---

### Post by zeroK on 2005-07-15
[QUOTE=varunus]I know this doesn't answer your question, but isn't evince in universe?  Or are you trying to compile a newer version?[/QUOTE]
 I'm trying to compile a newer version.

---

### Post by varunus on 2005-07-15
Did you try to install libgnomeui-dev from synaptic?  I know that package works, as it is installed for me...or is this the breezy version of the library?

---

### Post by zeroK on 2005-07-15
[QUOTE=varunus]Did you try to install libgnomeui-dev from synaptic?  I know that package works, as it is installed for me...or is this the breezy version of the library?[/QUOTE]
 Yes, and also through the shell. And I'm using the version for hoary. You've probably installed the package before the latest security release of libgnutls11 was released. This seems to have broken the depencies for libgnome2-dev which is a dependency of libgnomeui-dev.

---

### Post by zeroK on 2005-07-18
Quick solution:

apt-get source libgnutls11
mv gnutls11-1.0.16 gnutls11-1.0.16-13ubuntu1
cd gnutls11-1.0.16-13ubuntu1
fakeroot dpkg-buildpackage -b
cd -
sudo dpkg -i libgnutls11_1.0.16-13ubuntu1_i386.deb
sudo dpkg -i libgnutls11-dev_1.0.16-13ubuntu1_i386.deb

Not nice, but it works for me. An official solution would still be better ;)

---

