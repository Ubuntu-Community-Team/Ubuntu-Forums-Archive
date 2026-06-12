---
title: "adept-common upgrade marked broken"
date: 2007-04-05
forum: Repositories &amp; Backports
---

### Post by wwitzke on 2007-04-05
Hello everyone.  I'm a relatively new Kubuntu user (lots of experience with other *nix operating systems, though) using Edgy, and I hope you can help me.

This morning I went ahead and installed the latest set of upgrades for KDE and adept.  However, there are now three packages that are marked as broken.  Two of them I don't care about at all and have been broken for a while, but the third, adept-common, apparently has unresolved dependencies.  I downloaded and installed synaptic, based on recommendations in these forums, and it tells me, when I try to mark the package for upgrade:

> adept-common:
  Depends: konsole (>=4:3.5.5-0ubuntu3.3) but 4:3.5.5-0ubuntu3.2 is to be installed
  Depends: python-kde3 (>=3.15.2+20060422-2ubuntu4.3) but 3.15.2+20060422-2ubuntu4 is to be installed

apt-get tells me essentially the same thing when I run a simulated installation for adept-common.

I checked the dependencies, and I apparently don't have the option to upgrade konsole or python-kde.  I even disabled all universal and 3rd party repositories, refreshed the package list, and I still get the same dependency problem.

So, first, is this something I should even worry about?  Will this break the adept updater (which I still use, though I do like synaptic better)?  Will the number of broken packages continue to increase as I use Kubuntu?

Second, is there something wrong with my system that would prevent me from upgrading those packages, assuming that the dependencies listed for adapt-common are correct?  Or could this be a problem with that particular package listing the wrong dependencies?

Thanks :)

Wayne

---

### Post by wwitzke on 2007-04-05
Never mind :) .  It looks like I just jumped the gun here.  Other updates are now becoming available that are fixing these dependency problems.

Wayne

---

### Post by Gomek on 2007-04-05
Mine's still wondering where the crap python-kde3 is.

*edit:  It finally fixed itself.  :-D

---

