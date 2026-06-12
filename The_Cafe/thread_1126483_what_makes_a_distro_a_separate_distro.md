---
title: "what makes a distro a separate distro?"
date: 2009-04-15
forum: The Cafe
---

### Post by mamamia88 on 2009-04-15
lets face it all distros are based on the same kernel just customized to have a different gui and maybe a few minor tweaks under the hood.  so what exactly does it take for something to be reconginzed as a distro instead of someones highly customized variant of a distro?

---

### Post by BGFG on 2009-04-15
The only true separation to me is architecture, RPM, DEB, Binary, Source. After that it really doesn't matter to me. Then it just boils down to the talent of the development team and their taste in packages.

---

### Post by MaxIBoy on 2009-04-15
Like BGFG said, the major difference is package management (in other words, the method of installing software.)

The most common package formats are APT and RPM.

Debian and Debian-based distros use "APT" (Advanced Packaging Tool.) There are a lot of Debian-based distros, including Ubuntu. APT packages can be either binary (pre-compiled) or source (non-compiled.) However, I don't think you can install a source package and have it automatically compile.

RedHat/Fedora based distros use "RPM" (originally stood for RedHat Package Manager, now stands for RPM Package Manager.) Additionally, RPM has been accepted into the "Linux Standard Base," making it the "Standard" package format, so now a lot of non-RedHat-based distros use RPM as well. RPM is a binary package format.

Also, there are a few distros that have home-grown binary package formats. Puppy Linux is an example.

Many distros are source-based, meaning you compile everything. Some source-based distros have dependency handling and other advanced features you'd get with a binary-package distro, and the source code is automatically compiled whenever you install something. Examples include Slackware and Gentoo.


Keep in mind that tools such as Alien exist to convert between package formats; you can basically install any package on any system, with a varying degree of difficulty.





After the choice of package format, the next major difference between distros is the choice of default software, and the choice of software in the repositories (if the distro has repos at all.)

---

### Post by SomeGuyDude on 2009-04-15
It has to be a fundamentally different user experience, IMO. Otherwise Debian/Ubuntu are the same, and there's no difference between any of the RPM distros (Mandriva/SUSE/Fedora/etc). Give the user a different package manager, set up your own repos, control the release schedule, patch things as you see fit, that kinda thing.

It's why Crunchbang isn't a different distro, but Sabayon is markedly different from Gentoo. Built upon the same base, but heavily altered to change the way the user experiences it.

---

### Post by MaxIBoy on 2009-04-15
A good way to tell the difference is this:

Enable the Debian repositories under Ubuntu, and your system is toast. At best, you'd have a functioning virtual terminal.

However, CrunchBang uses the Ubuntu repos by default, so it isn't really its own distro. It's just a heavily customized Ubuntu setup.

---

### Post by Barrucadu on 2009-04-15
Package management, init system, and repositories are the main differences.

---

