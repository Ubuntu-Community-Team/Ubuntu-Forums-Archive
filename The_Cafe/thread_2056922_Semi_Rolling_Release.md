---
title: "Semi Rolling Release?"
date: 2012-09-12
forum: The Cafe
---

### Post by mamamia88 on 2012-09-12
Why doesn't Ubuntu do something like this?  Lock down important packages that are likely to cause breakage until they've been tested extensively and roll out constant updates for the applications?  What is the worst case scenario if i get a firefox bug?   I either rollback firefox or i use chrome until an update comes out and fixes it.     Is there any reason something like this wouldn't work?

---

### Post by whatthefunk on 2012-09-12
That is what they do, for the most part.  Everytime you do an update, you are getting important security and bug fixes and also updating certain programs.  If you want to update additional ones or make major upgrades, you can add ppas to your source list.  Next time you update, take a look at the update details to see what exactly is going on.  I get new versions of Firefox constantly.

---

### Post by mamamia88 on 2012-09-12
> **whatthefunk said:**
> That is what they do, for the most part.  Everytime you do an update, you are getting important security and bug fixes and also updating certain programs.  If you want to update additional ones or make major upgrades, you can add ppas to your source list.  Next time you update, take a look at the update details to see what exactly is going on.  I get new versions of Firefox constantly.

cool.   so why exactly do they need to come out with a new relase every 6 months?  Couldn't they just extensively test the new packages until they are almost 100% sure nothing will break?

---

### Post by whatthefunk on 2012-09-12
Because that way if you dont want to upgrade, you dont have to.  A lot of people dont like change and dont want to update to find something major like their DE upgraded.  Also, it provides a way to give support for a long amount of time, 5 years for LTS versions.  If they had a rolling release, this would be difficult.

---

### Post by mamamia88 on 2012-09-12
> **whatthefunk said:**
> Because that way if you dont want to upgrade, you dont have to.  A lot of people dont like change and dont want to update to find something major like their DE upgraded.  Also, it provides a way to give support for a long amount of time, 5 years for LTS versions.  If they had a rolling release, this would be difficult.

so why not just make it easy for the end user to lock the packages they don't want upgraded?   you could easily go into synaptic package manager and lock your desktop environment. And they could still do lts versions they would just have to setup the default repos properly.     for example on a regular install disc all repositories are enabled.    on an lts install disk only security repos are enabled by default.

---

### Post by snowpine on 2012-09-12
Most users want to be in control of when their applications get upgraded to a new version. What if, for example, your thesis is due tomorrow, but you log in to find out Ubuntu has automatically upgraded LibreOffice to a major new version that breaks your document formatting? Better to keep LibreOffice "frozen" (with bug fixes and security patches) at a stable version, then if a user wants a newer LibreOffice, they can [add the PPA]("https://launchpad.net/~libreoffice/+archive/ppa") at a convenient time (or just wait until 12.10 comes out next month).

---

### Post by mamamia88 on 2012-09-12
> **snowpine said:**
> Most users want to be in control of when their applications get upgraded to a new version. What if, for example, your thesis is due tomorrow, but you log in to find out Ubuntu has automatically upgraded LibreOffice to a major new version that breaks your document formatting? Better to keep LibreOffice "frozen" (with bug fixes and security patches) at a stable version, then if a user wants a newer LibreOffice, they can [add the PPA]("https://launchpad.net/~libreoffice/+archive/ppa") at a convenient time (or just wait until 12.10 comes out next month).

That has never happened to me but I can see your point.  But isn't reinstalling the next version of the os kind of a pain in the ***?    what I want basically is a stable base where stuff that i don't need to be 100% stable is updated automatically.   which i guess is what the lts version is + ppas.    Tell me is it possible to have a newer version of say unity on an older release?   For example can you have the 12.10 unity mods on 12.04?

---

### Post by snowpine on 2012-09-12
> **mamamia88 said:**
> That has never happened to me but I can see your point.  But isn't reinstalling the next version of the os kind of a pain in the ***?

If you have good backups, a separate /home partition, and [supported hardware]("http://www.ubuntu.com/certification/"), then you are looking at perhaps 1 hour tops, twice a year. I can assure you that people who use rolling release distros (like Arch) spend at least 2 hours a year administering their system. What do you consider a reasonable number of hours per year for system administration?

> **mamamia88 said:**
> what I want basically is a stable base where stuff that i don't need to be 100% stable is updated automatically.   which i guess is what the lts version is + ppas.    Tell me is it possible to have a newer version of say unity on an older release?   For example can you have the 12.10 unity mods on 12.04?

Yes, there is a [Unity PPA]("https://launchpad.net/~unity-team/+archive/ppa").

---

### Post by mamamia88 on 2012-09-12
> **snowpine said:**
> If you have good backups, a separate /home partition, and [supported hardware]("http://www.ubuntu.com/certification/"), then you are looking at perhaps 1 hour tops, twice a year. I can assure you that people who use rolling release distros (like Arch) spend at least 2 hours a year administering their system. What do you consider a reasonable number of hours per year for system administration?



Yes, there is a [Unity PPA]("https://launchpad.net/~unity-team/+archive/ppa").  you are right.   separate /home makes the whole process relatively straight forward.     Think I should write a script for adding all my regular programs and I'm good to go.

---

### Post by vexorian on 2012-09-12
> **mamamia88 said:**
> so why not just make it easy for the end user to lock the packages they don't want upgraded?   you could easily go into synaptic package manager and lock your desktop environment. And they could still do lts versions they would just have to setup the default repos properly.     for example on a regular install disc all repositories are enabled.    on an lts install disk only security repos are enabled by default.
It is actually already possible to lock package versions in synaptic.

If you use 12.04 LTS, it will last for 5 years. If you put PPAs for the apps you'd like to remain updated, then it will do exactly what you want it to do. You'll get firefox or LibreOffice updates whilst core packages stay basically the same (sans security fixes) until 2017.

---

### Post by snowpine on 2012-09-12
> **mamamia88 said:**
> you are right.   separate /home makes the whole process relatively straight forward.     Think I should write a script for adding all my regular programs and I'm good to go.

You can also upgrade (rather than fresh install) and then you won't have to reinstall all the regular programs.

Some users are divided on the upgrade vs. fresh install question, but the fact is that upgrades are fully supported and recommended by Canonical.

---

### Post by mamamia88 on 2012-09-12
> **snowpine said:**
> You can also upgrade (rather than fresh install) and then you won't have to reinstall all the regular programs.

Some users are divided on the upgrade vs. fresh install question, but the fact is that upgrades are fully supported and recommended by Canonical. how well would upgrading work from a minimal installation?  Say for example i create a command line script that will install my videodriver,xorg,wifi driver, xfce desktop, a display manager, synaptic, and a few apps.

---

### Post by snowpine on 2012-09-12
> **mamamia88 said:**
> how well would upgrading work from a minimal installation?  Say for example i create a command line script that will install my videodriver,xorg,wifi driver, xfce desktop, a display manager, synaptic, and a few apps.

It would be prudent to test it on a development box or virtual machine before applying to your production box, but in theory your approach seems sound. :)

---

### Post by mips on 2012-09-12
I'm not fond of apt pinning, it made my life a hell once with dependency issues.

Why not just switch to a distro that's rolling release?

---

### Post by mamamia88 on 2012-09-12
> **mips said:**
> I'm not fond of apt pinning, it made my life a hell once with dependency issues.

Why not just switch to a distro that's rolling release?

I already have but I was wondering for next time I get a new computer if i could save a lot of time doing a Ubuntu minimal install.  Or if i could possibly avoid installing stuff i don't use like ubuntu one, thunderbird, games, cd burning, software-center etc

---

### Post by mips on 2012-09-12
> **mamamia88 said:**
> I already have but I was wondering for next time I get a new computer **if i could save a lot of time doing a Ubuntu minimal install.  Or if i could possibly avoid installing stuff i don't use like ubuntu one, thunderbird, games, cd burning, software-center etc**

You mean as in a fresh minimal install?

---

### Post by mamamia88 on 2012-09-12
> **mips said:**
> You mean as in a fresh minimal install? yeah if i installed ubuntu minimal could i just apt-get install lightdm xfce4 xfce4-goodies and have a barebone xfce system without all the bundled apps with xubuntu-desktop?    And then could i remove epiphany replace it with chrome, install all my favorite apps without pulling in gnome/kde stuff?  or at least not more than nesscessary.

---

### Post by BrokenKingpin on 2012-09-12
> **whatthefunk said:**
> That is what they do, for the most part.  Everytime you do an update, you are getting important security and bug fixes and also updating certain programs.  If you want to update additional ones or make major upgrades, you can add ppas to your source list.  Next time you update, take a look at the update details to see what exactly is going on.  I get new versions of Firefox constantly.
Ubuntu is not even close to a semi-rolling release. The only time they update Firefox and user applications is if a security bug is found with that application. Even if they did update their packages through a release, it still would not be a semi-rolling release because they move to a new set of repos every 6 months for the new release, and the old release would not receive those application updates (unless security related).

Check out PCLinuxOS for a semi-rolling release distro.

[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

---

### Post by wheeze on 2012-09-12
> **mamamia88 said:**
> yeah if i installed ubuntu minimal could i just apt-get install lightdm xfce4 xfce4-goodies and have a barebone xfce system without all the bundled apps with xubuntu-desktop?    And then could i remove epiphany replace it with chrome, install all my favorite apps without pulling in gnome/kde stuff?  or at least not more than nesscessary.

That's about the only way I do installs anymore. Nothing installed that I don't want or need. You won't even have to remove Epiphany because it won't be installed in the first place :D

---

### Post by mips on 2012-09-12
> **mamamia88 said:**
> yeah if i installed ubuntu minimal could i just apt-get install lightdm xfce4 xfce4-goodies and have a barebone xfce system without all the bundled apps with xubuntu-desktop?    And then could i remove epiphany replace it with chrome, install all my favorite apps without pulling in gnome/kde stuff?  or at least not more than nesscessary.

Yes. I did that just a few days ago with Quantal as I don't like the full/default install of Xubuntu. I did a cli/base install and then just added xfce4, some other apps I use and the greybird theme. It's also much leaner/faster than a default install.

Try it out for yourself it's really easy and the mini iso is only 30MB.

12.04 mini.iso:
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

12.10 beta mini.iso
[http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/)

A bit later (12.10 release) I'm gonna try and remaster the mini.iso to include all the packages in my apt cache so I wont have to download them again just in case of an emergency (I have slow internet & limited bandwidth)

---

### Post by mamamia88 on 2012-09-12
> **mips said:**
> Yes. I did that just a few days ago with Quantal as I don't like the full/default install of Xubuntu. I did a cli/base install and then just added xfce4, some other apps I use and the greybird theme. It's also much leaner/faster than a default install.

Try it out for yourself it's really easy and the mini iso is only 30MB.

12.04 mini.iso:
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

12.10 beta mini.iso
[http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/)

A bit later (12.10 release) I'm gonna try and remaster the mini.iso to include all the packages in my apt cache so I wont have to download them again just in case of an emergency (I have slow internet & limited bandwidth)

i would if i finally didn't get this arch install perfect.   i'm on a netbook and tried a vm with 512mb allotted but even that was too slow for me.  i eventually just quit virtualbox and uninstalled it.     but yeah as long as i have a wired connection and a command prompt no reason not to do it.   does aptitude have a feature like pacman where you can chose part of meta packages?

---

### Post by snowpine on 2012-09-12
Yay Arch!

---

### Post by whatthefunk on 2012-09-12
> **BrokenKingpin said:**
> Ubuntu is not even close to a semi-rolling release. The only time they update Firefox and user applications is if a security bug is found with that application. Even if they did update their packages through a release, it still would not be a semi-rolling release because they move to a new set of repos every 6 months for the new release, and the old release would not receive those application updates (unless security related).

Check out PCLinuxOS for a semi-rolling release distro.

[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

Good point about the separate repos.  Does make it a definite non-rolling release.

---

### Post by mips on 2012-09-13
> **mamamia88 said:**
>   does aptitude have a feature like pacman where you can chose part of meta packages?

Not sure but I know many meta packages are simply made up of single packages which you can install normally, you can also install the core of meta package and leave out the recommended stuff with the --no-recommends option.

I installed [pacapt]("http://lifehacker.com/5880003/pacapt-brings-arch-linuxs-amazing-pacman-package-manager-to-other-linux-distributions-well-sort-of") the other day and it's pretty cool to use the pacman syntax to interface with apt.

---

### Post by Jakin on 2012-09-13
> **vexorian said:**
> It is actually already possible to lock package versions in synaptic.

And for anyone wanting to use Muon, right click on a package name and you can lock it, took me awhile to figure this out, as simple as it was.

---

