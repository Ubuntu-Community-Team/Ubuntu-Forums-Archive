---
title: "back-ports directories are empty"
date: 2005-10-05
forum: Ubuntu Backports
---

### Post by cytoplasm on 2005-10-05
Some time ago I replaced my back-ports URL within sources.list with what has been recommended:
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
I recently tried to install beagle which was part of back-ports universe.  Now, I'm told this package doesn't exist.  So, I meandered over to the new URL ( [http://archive.ubuntu.com/ubuntu/dists/hoary-backports/](http://archive.ubuntu.com/ubuntu/dists/hoary-backports/) ) and noticed that there are no deb packages in any of the directories.  They are empty.  What gives?  What is the purpose of having back-ports if we have nothing there?

---

### Post by aysiu on 2005-10-08
Are you sure they're empty? Maybe they're just zipped up?

---

### Post by imagine on 2005-10-09
[QUOTE=cytoplasm]Some time ago I replaced my back-ports URL within sources.list with what has been recommended:
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse[/QUOTE]It is still recommended :)


[QUOTE=cytoplasm]I recently tried to install beagle which was part of back-ports universe.  Now, I'm told this package doesn't exist.[/QUOTE]Beagle is in hoary universe.
Which version are you searching? I think there were some problems with the backported version from Breezy and it got removed.
Besides most of the effort is put now in the breezy repositories as it seems, although it's still unstable for some more days. So some packages may indeed be missing from hoary-backports.

[QUOTE=aysiu]Are you sure they're empty? Maybe they're just zipped up?[/QUOTE]No they aren't empty.

---

### Post by jdong on 2005-10-09
They are not empty -- the archive.ubuntu.com systems use **pooled repositories**, meaning that all the software lies in a pool folder. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=beagle](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=beagle)

There is currently no *official* Beagle backport. After a bit of work with the Mono maintainers, we concluded that there existed no good, solid ways of porting the Breezy Mono system back to Hoary. 

For beagle users, I highly suggest upgrading to Breezy when it's released next week :)

---

### Post by cytoplasm on 2005-10-13
jdong,

Thanks for the info.  I'll upgrade to Breezy in a few weeks. :D

---

