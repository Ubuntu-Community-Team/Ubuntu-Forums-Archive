---
title: "How Does Rolling Release Work When There's Huge Changes"
date: 2011-11-23
forum: The Cafe
---

### Post by user1397 on 2011-11-23
I was just wondering how you manage a rolling release distribution when there are huge software changes, such as the transition from gnome 2 to 3 (as an example, what did arch users do about the gnome transition?)

What I mean is, in a standard release model like ubuntu, you don't have to worry about incompatibilities or the like when upgrading especially if you do a clean install, but if you have a rolling release distro which is constantly updating itself, wouldn't the upgrade of major software changes break a bunch of stuff and basically make you want to install from scratch again? 

This is coming from someone who has not ever used a rolling release distro, other than for a very brief period of time.

---

### Post by Bachstelze on 2011-11-23
I don't know about Arch, but other so-called "rolling release" distros like Debian Sid and Gentoo **do not** always make new software available right off. For example, Gentoo never had packages of KDE 4.0 because it was too unstable, KDE 4 appeared in Gentoo with 4.1.

"Rolling release" does not mean you always get the latest software.

---

### Post by cgroza on 2011-11-23
I do not really know the answer to this question, but I think that changes are made step by step, and the differences are not as great as in a release cycle similar to Ubuntu's, which minimizes the incompatibilities.

---

### Post by Bachstelze on 2011-11-23
Basically, if the distro devs think introducing a new version of a package would break too many things, they just don't until they or a new upstrem version have fixed them. (How many is too many depends on the distro, and most also have a "stable" and an "unstable" branch.)

---

### Post by 3Miro on 2011-11-23
The short answer is: same as upgrading from one Ubuntu release to another. On a big upgrade, you just get more packages that you need to update. Depending on the distro, you may have to manually fix some settings.

The longer answer is that the software packages can be sub-divided into software groups. For example you have XFCE 4.6 and 4.8, both come with their own versions of the XFCE programs and library dependence. When you upgrade you just upgrade all at once. This is independent from say general Xorg set of libraries and drivers. Another set of packages is the individual programs like Firefox. The ideas is that the sub-groups of packages can be upgraded independently.

---

### Post by Tibuda on 2011-11-23
Arch have a separate "testing" repository for bugtesters to report incompatibility and such. Stuff are only available for everyone after some time in the testing repos. 
[http://www.archlinux.org/news/gnome3-in-testing/](http://www.archlinux.org/news/gnome3-in-testing/)
[http://www.archlinux.org/news/gnome3-in-extra/](http://www.archlinux.org/news/gnome3-in-extra/)

---

### Post by angryfirelord on 2011-11-23
> **ubuntuman001 said:**
> I was just wondering how you manage a rolling release distribution when there are huge software changes, such as the transition from gnome 2 to 3 (as an example, what did arch users do about the gnome transition?)

What I mean is, in a standard release model like ubuntu, you don't have to worry about incompatibilities or the like when upgrading especially if you do a clean install, but if you have a rolling release distro which is constantly updating itself, wouldn't the upgrade of major software changes break a bunch of stuff and basically make you want to install from scratch again? 

This is coming from someone who has not ever used a rolling release distro, other than for a very brief period of time.
It depends on how the distro manages its package updates. For instance, in Debian Sid, if something is shown to cause some significant breakage, they won't include it. That's why Sid is still at KDE 4.6 even though KDE 4.7 is out now. Other distros like Arch are a bit more lenient in their package testing, so you'll get newer software, but things break more often over there.

---

### Post by LowSky on 2011-11-23
> **ubuntuman001 said:**
> I was just wondering how you manage a rolling release distribution when there are huge software changes, such as the transition from gnome 2 to 3 (as an example, what did arch users do about the gnome transition?)

What I mean is, in a standard release model like ubuntu, you don't have to worry about incompatibilities or the like when upgrading especially if you do a clean install, but if you have a rolling release distro which is constantly updating itself, wouldn't the upgrade of major software changes break a bunch of stuff and basically make you want to install from scratch again? 

This is coming from someone who has not ever used a rolling release distro, other than for a very brief period of time.


Arch has a few levels of packages: core, extra, testing, community. Things in core are the most stable, extra contains things not so perfect, and/or have pseudo licensing issues, like mp3 playback. testing and community have programs still not perfect or not tested by the developers.

Big changes often involve an extra step or two, like deleting a system file before upgrading for instance the latest big update you needed to delete the /etc/profile.d/locale.sh file.

Things usually go pretty easy. I usually update once a week.

---

### Post by 3Miro on 2011-11-23
> **LowSky said:**
> Arch has a few levels of packages: core, extra, testing, community. 

I have a question. In Arch, is there a way to say use core for all your packages, but only install individual programs form testing. For example, in Gentoo you have the regular stable repository with Firefox 3.6, however, I wanted to use a newer version so I said that I wanted to use FF from unstable. I had to specify FF and couple of other packages (dependencies), but in the end, I am using the latest "unstable" FF while at the same time I have all the rest of my system as "stable".

---

### Post by SadisticCheeto on 2011-11-23
> **3Miro said:**
> I have a question. In Arch, is there a way to say use core for all your packages, but only install individual programs form testing. For example, in Gentoo you have the regular stable repository with Firefox 3.6, however, I wanted to use a newer version so I said that I wanted to use FF from unstable. I had to specify FF and couple of other packages (dependencies), but in the end, I am using the latest "unstable" FF while at the same time I have all the rest of my system as "stable".
What you described can certainly be done, but the developers don't recommend it. Cherry picking from the testing repository increases the chances of breakage, but if you really know what you are doing, you can get away with it. However, if there does end up being a problem, you will most likely be on your own unless you use all of the packages that are in testing like the developers expect. The forums could still be of help if there is a problem, though.

An alternative would be to use ABS to update the package's PKGBUILD if you can't wait for an updated package and don't want to use all of testing just for the latest version of your favorite program. Of course, you could also go to the AUR. [Here](https://aur.archlinux.org/packages.php?ID=48216) is an example for the Aurora channel for Firefox. In that specific example, there is also a unofficial user repository that maintains binary packages for Aurora. There are other repositories like that that contain binary packages for many packages in the AUR if a user doesn't want to go through compiling the package. [Here](https://wiki.archlinux.org/index.php/Unofficial_User_Repositories) is the list.

---

### Post by 3Miro on 2011-11-23
> **SadisticCheeto said:**
> What you described can certainly be done, but the developers don't recommend it. Cherry picking from the testing repository increases the chances of breakage, but if you really know what you are doing, you can get away with it. However, if there does end up being a problem, you will most likely be on your own unless you use all of the packages that are in testing like the developers expect. The forums could still be of help if there is a problem, though.

An alternative would be to use ABS to update the package's PKGBUILD if you can't wait for an updated package and don't want to use all of testing just for the latest version of your favorite program. Of course, you could also go to the AUR. [Here](https://aur.archlinux.org/packages.php?ID=48216) is an example for the Aurora channel for Firefox. In that specific example, there is also a unofficial user repository that maintains binary packages for Aurora. There are other repositories like that that contain binary packages for many packages in the AUR if a user doesn't want to go through compiling the package. [Here](https://wiki.archlinux.org/index.php/Unofficial_User_Repositories) is the list.

I see. I guess Arch is too close to the latest software for this to matter. Gentoo has a very natural way of upgrading only selected packages (i.e. like a program and its dependencies). This happens often, other than the Firefox example that I gave, I can think of KDE 4.5 that had a bug in the Kmail package and never went stable (now you can get 4.6 stable or 4.7 unstable), but people could use 4.5 it by activating a bunch of packages from unstable. Right now, you can only get Compiz as unstable, same goes for AWN, code::blocks, skype, flash, Firefox >= 4.0 and the latest kernel (>= 2.6.39). The only versions of Gnome available are Gnome 2.32 and Gnome 3.2.

PS: I am using XFCE 4.8, which was available as stable like a month after its release.

---

