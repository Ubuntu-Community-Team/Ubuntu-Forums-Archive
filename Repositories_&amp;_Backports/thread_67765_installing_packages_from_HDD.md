---
title: "installing packages from HDD"
date: 2005-09-21
forum: Repositories &amp; Backports
---

### Post by markr on 2005-09-21
I've just installed Breezy (preview) on my laptop which does not have internet connectivity yet (until I get my wireless working).

In order to install my Nvidia driver I need to install gcc 3.4, which I've downloaded from another machine and copied to my laptop.

What I need to know is how do I install the debs without connecting to a repository (or how do I set my HDD as a repository)?

Thanks

Mark.

---

### Post by agm642 on 2005-09-21
You can install packages without an internet connection using the command "dpkg -i <package name>. As for the second option, you can copy the files to /var/cache/apt/archives and then install them using apt-get or any package manager.

---

### Post by tonym on 2005-09-21
Im not at an Ubuntu machine so can't check if its still there but Debian used to have some info on this at /usr/share/doc/apt/offline.html 

Regards

Tony

---

