---
title: "Q re: packages to be updated/security updates"
date: 2009-08-24
forum: Server Platforms
---

### Post by submute on 2009-08-24
Whenever I login to my ubuntu server, I see:

5 packages can be updated.
10 updates are security updates.

So I sudo apt-get upgrade, but then see:

The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

And but so nothing is ever updated. Why are these packages kept back, and why does it tell me there are packages to be updated when it doesn't want to seem to update anything?

thanks!

---

### Post by kgeekworking on 2009-08-24
Kept back means that there are some other installed packages that depend upon the program (in your case the kernel).  It will not be updated because doing so can make the other programs stop working.

Apt is more focused on not breaking anything so it is not to aggressive in trying to resolve these conflicts.  You should have aptitude installed by default.  Aptitude basically does the same thing as apt except it works a bit harder to try to offer suggestions to resolve these types of conflicts.

At least in my experience, aptitude will usually fix a kept back kernel.  The usage is pretty much the same:

sudo aptitude update
sudo aptitude upgrade

---

### Post by Bachstelze on 2009-08-24
[http://ubuntuforums.org/showthread.php?t=1191493&page=2#11](http://ubuntuforums.org/showthread.php?t=1191493&page=2#11)

(Yes, I'm lazy. :p)

---

