---
title: "Please backport emacs-snapshot-gtk from gutsy: feisty version is severely broken."
date: 2007-05-11
forum: Ubuntu Backports
---

### Post by sergio.callegari on 2007-05-11
Feisty seems to ship with a completely broken emacs-snapshot-gtk.

See  [https://bugs.launchpad.net/ubuntu/+source/emacs-snapshot/+bug/94777](https://bugs.launchpad.net/ubuntu/+source/emacs-snapshot/+bug/94777)
I do not know if it happens on every possible system, but on some it systematically segfaults at startup.

The version in gutsy, namely

emacs-snapshot-gtk_20070302-1_i386.deb
emacs-snapshot-bin-common_20070302-1_i386.deb
emacs-snapshot-common_20070302-1_all.deb

appears to be fine and can be installed cleanly on feisty (all the dependencies are there).

Please make it available asap through the backports or the updates, since it is not nice to have an important application that segfaults in the distro (and it is an important application - it is indicated as a snapshot, but it is in fact now very stable, and what most people wants to run because of the new features and the antialiased fonts).

---

### Post by aikishugyo on 2007-05-17
In the meanwhile (I wouldn't hold my breath waiting for the Ubuntu people to do anything about this):

[http://peadrop.com/blog/category/computers/emacs/](http://peadrop.com/blog/category/computers/emacs/)

Compilation worked perfectly flawlessly on my AMD64 system, if you have an i386 system none needed. Works perfectly for me, all the broken functionality in the Edgy snapshot is just a bad dream now. Combined with the TeXLive DVD installation I am in heaven.

---

