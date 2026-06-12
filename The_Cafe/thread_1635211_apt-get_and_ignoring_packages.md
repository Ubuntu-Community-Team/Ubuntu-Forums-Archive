---
title: "apt-get and ignoring packages"
date: 2010-12-01
forum: The Cafe
---

### Post by del_diablo on 2010-12-01
I had my Debian box working the other day, so I set it to be my blender-svn box, and I happely compiled down and set up a build script.
The other day I updated to sid and set up apt with pinning. Since I have a ATI card, I use a lot of the experimental mesa and radeon packages.
Now, during installtion, at some point I removed freeglut3-dev and similar packages needed to compile blender.
The packages(glut,freeglut,etc) depends on what is a sub version lower than what I have installed, but I can't seem to solve this.
Since the packages are missing from experimental, I can't get them from there either, I need to use the sid packages :(
The sid packages needs other sid packages, they are by dependency hardset to require the bundled sid packages.
So..... what is the command for installing a package and ignoring its dependencies? 
Since the version number is more or less quite identical, I doubt there will be a package break in terms of system function.

---

### Post by del_diablo on 2010-12-02
*bump*

---

### Post by v41 on 2010-12-02
Judging from the man page, it seems that dpkg can do what you want.  For a summary of the relevant options, type the following in a terminal,
> dpkg --force-help

---

### Post by del_diablo on 2010-12-02
I figured it out.
Basically package needed package 2, package 2 was actually a link package, and several libs on the side could be upgraded. The required package was found with *aptitude search '~Plibgl-dev'*.
Sadly there is no actual way of ignoring packages, the closest you get is to download the package manually, and then hoping you can use enough --force-flags.

---

