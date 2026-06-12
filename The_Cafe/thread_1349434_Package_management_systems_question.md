---
title: "Package management systems question"
date: 2009-12-08
forum: The Cafe
---

### Post by Cuddles McKitten on 2009-12-08
Are distros built around their package management systems, or could an Ubuntu user install yum or pacman?  I see they're available through APT, but I'm too afraid that I'll break something by testing my hypothesis. :(

As a follow-up, if people on an RPM-based distro can use a .DEB-based package manager, then why don't more people branch out from their distro's default?  Is it just that complications can occur as a result?

---

### Post by liamnixon on 2009-12-08
Yes, you can install alternate package managers on an OS.  However, I'm pretty sure it's a lot of work for little payoff.

---

### Post by Xbehave on 2009-12-08
I think distros are always built around a single package manager (dpkg or rpm are the most common) because it has to keep track of all the installed files, so even if you install software from the another format there needs to be a tool to translate the metadata and inform the real package manager (such as alien).

As for your 2nd question, the more 3rd party software you have the less tested/reliable your install is and the translation process isn't perfect either so it's safer to stick to:
1) your 1st party repos
2) 3rd party repos in the normal format
3) compiled software you install through the package manager (tools like check-deb are pretty well tested)

---

### Post by Dragonbite on 2009-12-08
I believe PCLinuxOS is an RPM based distro that uses Synaptic.

---

