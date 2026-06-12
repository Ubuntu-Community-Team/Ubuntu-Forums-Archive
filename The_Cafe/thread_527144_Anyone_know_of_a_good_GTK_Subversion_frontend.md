---
title: "Anyone know of a good GTK Subversion frontend?"
date: 2007-08-16
forum: The Cafe
---

### Post by ThinkBuntu on 2007-08-16
I'm interested in using Subversion for some of my web development, and would like to use a GTK frontend for it. I'm also open to other options (Mercurial, CVS, etc.), but it seems like Subversion's the most popular (or fastest growing) free version control these days.

---

### Post by reclusivemonkey on 2007-08-17
Can't vouch for it, but you can try this (its in its infancy);

[http://gsvn.sourceforge.net/](http://gsvn.sourceforge.net/)

---

### Post by scooper on 2007-08-17
I settled on svn-workbench as the best.  Dependencies include python stuff and wxgtk, so it brings in a bit more than just gtk.  But it could be worse.  I've had no major issues with it, other than it prevents me from learning the svn command line. :)

```
Package: svn-workbench
Priority: optional
Section: universe/devel
Installed-Size: 1516
Architecture: all
Version: 1.5.1-0ubuntu1
Depends: python-central (>= 0.5.8), python-svn (>= 1.5.1), python-wxgtk2.6
Filename: pool/universe/s/svn-workbench/svn-workbench_1.5.1-0ubuntu1_all.deb
Size: 526692
Description: A Workbench for Subversion
 pysvn-workbench is a workbench (graphical client) for the subversion
 revision control system, written in the Python language.

```

---

### Post by Mr. Picklesworth on 2007-08-18
Best one I have used is the version control add-in for MonoDevelop. It's pretty baffling how few decent, graphical SVN and CVS clients there are, though.
I have tried piles of them, and I would say 90% of them were terrible! (One of them actually crashed, from the very beginning, on three machines and two platforms that I tested it on). Either ugly user interface, slowness, crashiness, or all three.

The only two I have enjoyed using (or been able to use) have been in really weird places: That MD add-in and Tortoise SVN (which is a Windows Explorer extension).

---

### Post by Vadi on 2009-06-02
gsvn seems dead, no release in 3 years. Going to check out Monodevelop.

There is NautilusSVN that's quite great, but I don't like the burden of it always running.

---

### Post by Tibuda on 2009-06-02
Don't forget meld. It is a graphical diff viewer compatible with svn, git, bzr, cvs, mercurial...

---

### Post by pHr34kY on 2010-08-26
NautilusSVN has become [RabbitVCS]("http://wiki.rabbitvcs.org/wiki/install/ubuntu")

There's an Ubuntu apt repo for it (see above link), and integrates quite nicely in gnome, and from first impression looks a lot like TortoiseSVN.

---

### Post by Ozor Mox on 2010-08-26
I've heard that [RapidSVN](http://rapidsvn.tigris.org/) is good. No idea if it's GTK or not.

---

