---
title: "problem with sources list"
date: 2005-06-18
forum: Repositories &amp; Backports
---

### Post by carlc on 2005-06-18
what's wrong here?

when I run apt-get update, I get this error:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)


here is the entry is my sources list:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Xian on 2005-06-18
This is not a local issue and so you have no control over that error message. The problem resides on the marillat server. The appropriate action to take is to remove those repos from your sources.list until such time that this incident is corrected.

---

