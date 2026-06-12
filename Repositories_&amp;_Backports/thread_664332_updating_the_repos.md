---
title: "updating the repos"
date: 2008-01-11
forum: Repositories &amp; Backports
---

### Post by Circus-Killer on 2008-01-11
i've seen 5 different threads so far, all asking the same thing, none with a straight forward answer.

recently checkgmail stopped working. now the latest svn version works fine. so what i want to do is build and package a .deb from the svn version. i dont need help with that.

but once i have got the .deb, how do i submit it to be added to the repos. i know that svn versions shouldnt be used to build the packages, but right now the version of checkgmail thats in the repos doesn't work at all. i figure rather have a working version based on the svn version, rather than having a "stable" package that does not work at all.

so, is there anyway i can submit the new .deb that i will be creating, so that others may benefit from it?

---

### Post by Circus-Killer on 2008-01-11
*bump*

---

### Post by Circus-Killer on 2008-01-16
*one last bump*

---

### Post by kostkon on 2008-01-16
You can become a member at [Launchpad]("http://launchpad.net/") and start you own [*personal package archive*]("https://help.launchpad.net/PPAQuickStart") (i.e. *your own personal repository*) and then offer it to the people. How cool is that?

The packages are automatically built against any still supported version of Ubuntu and any architecture supported. You only need to provide source packages.

---

