---
title: "ubuntu-desktop package"
date: 2005-11-15
forum: The Cafe
---

### Post by cbudden on 2005-11-15
If people are removing things that ubuntu-desktop depends on, and they see that the Ubuntu desktop is going to be remove, should there be some message come up that this is not the case, because it isn't.

---

### Post by Kvark on 2005-11-15
Yeah, soon after switching to Ubuntu I tried to uninstall Evolution and it said it had to remove the whole Ubuntu desktop environment to get rid of Evolution. As a fresh newbie I just assumed it was the same thing as with Windows needing Explorer.

---

### Post by TravisNewman on 2005-11-15
ubutu-desktop is a meta-package. You can remove it without incident. 

If you ever want to upgrade using apt instead of reinstalling from CD, you may have problems if that meta-package isn't installed, but other than that, all it is is a package that depends on other packages.

---

### Post by Kvark on 2005-11-15
Yeah panickedthumb, and I think cbudden's point was that newbies don't know that so there should be a message there that explains what it is.

---

### Post by ssam on 2005-11-15
[https://launchpad.net/distros/ubuntu/+spec/default-package-groups](https://launchpad.net/distros/ubuntu/+spec/default-package-groups)

"Removing Default Programs - better mechanism to remove programs included in the default installation. Not removing ubuntu-desktop, maybe somehow remembering this is a default installation minus program removed, so you won't have problems when upgrading to a new distro version."

looks like possible for dapper if someone does the work for it. if you felt it was really important make a [bounty]("https://launchpad.net/distros/ubuntu/+bounties").

---

### Post by TravisNewman on 2005-11-15
[QUOTE=Kvark]Yeah panickedthumb, and I think cbudden's point was that newbies don't know that so there should be a message there that explains what it is.[/QUOTE]
oh sorry, I misunderstood both of your points ;)

They've already done some work on it if I recall correctly.

---

### Post by aysiu on 2005-11-15
Synaptic's description of the package says: > It is safe to remove this package if some of the desktop system packages are not desired.

---

