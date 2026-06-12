---
title: "Aptitude rocks!"
date: 2006-08-21
forum: The Cafe
---

### Post by mostwanted on 2006-08-21
I have a bunch of non-official repos in my APT sources which sometimes cause depedency issues (newer versions of libraries than certain official packages expect). Because they've caused some issues in the past, I've had to remove the metapackage ubuntu-desktop.

So after an upgrade yesterday, the update manager, Synaptic, add/remove and all those other graphical APT programs, stopped working because of some of these dependency problems. Ubuntu-desktop couldn't be installed using apt-get (neither could it using Synaptic back when it worked), so I tried Aptitude to see if it could solve my problems...

By selecting ubuntu-desktop for install, Aptitude properly downgrades the packages causing problems, but only those, so my system is fully functional. Truly great dependency solving and even provides a curses GUI comparable to Synaptic; I'm an Aptitude convert now.

---

### Post by mips on 2006-08-21
Aptitude I find less stable than synaptic but it gets the job done in Kubuntu.

---

### Post by Rackerz on 2006-08-21
Aptitude seems to install dependencies when it finds an install needs them whereas apt-get doesn't for me.

---

### Post by saracen on 2006-08-21
[There is a spec]("https://features.launchpad.net/distros/ubuntu/+spec/dependency-removal") to resolve this issue nicely in Edgy.  The wiki page is [here]("http://wiki.ubuntu.com/PackageDependencyManagement") as well.  There's a beta version of the improved apt-get out already so it looks like this will most likely make it into the release.

---

