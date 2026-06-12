---
title: "update issues in 13.10"
date: 2013-06-26
forum: Ubuntu Development Version
---

### Post by Deucalion29710 on 2013-06-26
When I run my Software Updater it seems like it infinitely searches for updates.  Upon timing out it will then tell me how much it needs to download.  When I run sudo apt-get update I get tons of 404 errors from saucy main (it appears to be).  The complete output of get-update is as follows:

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/saucy/contrib/binary-amd64/Packages](http://download.virtualbox.org/virtualbox/debian/dists/saucy/contrib/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/saucy/contrib/binary-i386/Packages](http://download.virtualbox.org/virtualbox/debian/dists/saucy/contrib/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.



So I removed the VirtualBox and the Cairo PPAs.  Software Updater now works although there is an update (Ubuntu Base) that it will not let me select.  It seems the same was the case in 13.04.  Strange and mildly annoying.


Would somebody please help me figure out what the correct PPAs are for these applications?  Also, the distro of 13.10 is one of the daily builds from a couple of weeks ago.  Should this distro upgrade itself as other builds are uploaded?

---

### Post by dino99 on 2013-06-26
you need to check that these ppas exist for "saucy" (for example, virtualbox only have "raring" as its more recent release)

---

### Post by oldos2er on 2013-06-26
Moved to Ubuntu +1.

---

### Post by deadflowr on 2013-06-27
> **dino99 said:**
> you need to check that these ppas exist for "saucy" (for example, virtualbox only have "raring" as its more recent release)

Exactly.
A repository needs to exists for you to be able to pull from it.

Best to disable those ppa's.
Or try switching them to the raring repos.

The former is safer.
The latter is truly up in the air on what might happen.

---

