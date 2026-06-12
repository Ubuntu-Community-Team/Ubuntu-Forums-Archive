---
title: "Debian repositories keys"
date: 2007-03-02
forum: Repositories &amp; Backports
---

### Post by x1a4 on 2007-03-02
Hi,

I want to add Debian's repositories to my _sources.list_.  Does anybody know the URLs to download the Debian keys?  

I want the following keys: 

A70DAF536070D3A1
F1D53D8C4F368D5D
A70DAF536070D3A1
B5D0C804ADB11277

Thank you.

---

### Post by Kateikyoushi on 2007-03-02
I do the following to get the keys.

gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

---

### Post by x1a4 on 2007-03-02
Awesome.  Thank you.

---

### Post by az on 2007-03-02
You don't want to mix ubuntu and debian repositories.  Ubuntu and debian are not binary-compatible.

You need to either remove all the ubuntu ones or all the debian ones.  Make sure you dist upgrade to the highest version of libc.

Use the source repos, if you want, but don't try to run debian packages on Ubuntu.

---

