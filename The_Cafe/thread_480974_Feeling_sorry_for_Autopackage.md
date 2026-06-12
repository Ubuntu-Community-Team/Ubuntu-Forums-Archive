---
title: "Feeling sorry for Autopackage"
date: 2007-06-22
forum: The Cafe
---

### Post by Canis familiaris on 2007-06-22
The Autopackage project at sometime last year looked promising and flourishing. However disagreements among the Debian Developers with Autopackage developers and lack of support for DPKG in Autopackage has prevented its growh. I know Autopackage has problems and installing by APT is much more superior and secure, but I can't help feeling sad for the Autopackage projct. There is hardly any development now and no one has posted into the Autopackage forums for months now. I feel that Autopackage is a great way to install third party software which are not available by apt-get.
One of the facts - a bitter fact - that has slowed growth of Linux is no uniform way of installing third party software. Yes the packages supported by APT or YUM(in RPM) is arguably easier installation that most, but commercial vendors would not set up apt-get repos as well as rpm installers - and installers for hundred of distros around. Likewise developers of a distro are not expected to build packages for each commercial software - the answer for them is Autopackage.
I know Autopackage will NOT be integrated in Gutsy nor Gutsy+1 nor even Gutsy+2, and neither do I want but I believe in its potential but the Autopackage project has slowed down and I fear like many OSS projects it may die.:(
I feel it needs integration with dpkg and rpm and someone needs to do this. I being not an expert has not idea but only hope someone gets up and and helps the developers.
What do you think?

---

### Post by tehkain on 2007-06-22
I never understood autopackages approach to the situation. They should have focused on enhancing existing package systems to work with some type of map. That map defines what OS uses what files and they get passed on to DKPG and the rpm counter part.

So you would load up a .AP file with dpkg and it looks at the map. Matches the OS. Matches dependencies. Then installs it as a normal deb. It was probably the hard approach but I think it would be the better one.

---

### Post by az on 2007-06-22
AFAIK, the fundamental problem with autopackage is that all of upstream must buy into it.  You just can't realistically get all of upstream to build their software in a way that's friendly to autopackage.

---

