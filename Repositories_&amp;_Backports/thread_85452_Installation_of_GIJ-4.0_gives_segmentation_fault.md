---
title: "Installation of GIJ-4.0 gives segmentation fault"
date: 2005-11-02
forum: Repositories &amp; Backports
---

### Post by Aflex on 2005-11-02
Hi,

I tried installing eclipse today, and, not suprisingly, it required some additional packages to be installed. Gij-4.0 was one of these, but gave a segmentation fault failing the entire eclipse installation.

```

Setting up gij-4.0 (4.0.1-4ubuntu9) ...
/var/lib/dpkg/info/gij-4.0.postinst: line 10: 11788 Segmentation fault      gcj-dbtool-4.0 -n /var/lib/gcj-4.0/classmap.db
dpkg: error processing gij-4.0 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gij-4.0

```

I tried to find the file mentioned in the error message and it appeared to be non-existing. So I went ahead badly and 'touched' it, which made the installation going smoothly. 

However! gij-* is now segmenting on me. Eclipse seems to be running fine, but I don't think it installed gij just for the hack of it. I'm just wondering a) what could have caused the problem and b) how can I reinstall gij-4.0 without it throwing errors at me?

---

### Post by JonathanRRogers on 2008-07-23
I just ran into nearly the exact same problem in Ubuntu 8.04 (Hardy). I used the command "sudo apt-get build-dep subversion" rather than trying to install Eclipse and the problem for me was with gij-4.2. I touched "/var/lib/gcj-4.2/classmap.db" and the install succeeded. I also couldn't figure out how get the debugging output you provide. How did you get it to show the exact command and location in the script that failed?

---

