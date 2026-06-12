---
title: "How do I make a repository?"
date: 2008-12-11
forum: Ubuntu Customization Guide
---

### Post by Kopachris on 2008-12-11
There are a few things that I want to include in my Ubuntu-based distro, but they aren't in the Ubuntu repositories.  It's things like Rosegarden, the latest LilyPond, OpenOffice.org 3, XBMC, and VirtualBox Open.  Some things are because I want to keep up with the latest version (like LilyPond, Rosegarden, and OOo), and some are because I have custom setup instructions (like VBO).  How would I go about making a deb repository so the update manager can automatically update these?:confused:

Basically what I want to know is if I need any special software server-side so apt can read it.  I also need to know about the file hierarchy, and if there are any special configuration files I need.

---

### Post by Bluebell392 on 2008-12-30
There is software to make setting up a Debian/Ubuntu repository easy(or at least easier than doing it manually). You can get it from the Ubuntu repositories with sudo apt-get install reprepro. This article contains the information to setup everything using the software.[Setting up your own APT repository with upload support]("http://www.debian-administration.org/articles/286")

---

### Post by Kopachris on 2008-12-30
Thank you!  That's exactly what I needed! :D

---

