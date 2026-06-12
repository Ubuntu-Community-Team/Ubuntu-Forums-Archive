---
title: "Default repository script (Solved)"
date: 2005-11-15
forum: Repositories &amp; Backports
---

### Post by ch13f121 on 2005-11-15
what's the default repo script, can anyone post it for me to copy paste? better yet, can anyone give me the repository with the backports on it? I'm using breezy badger, and I messed up my repo :rolleyes:

---

### Post by Mustard on 2005-11-15
A standard breezy would be like this one;

[http://paste.ubuntulinux.nl/2325](http://paste.ubuntulinux.nl/2325) (note it has a hoary backports repo in it, but its commented out)

To make a new one try this link;

[http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)

This is mine contructed using the link above (note that it will construct the sources.list with the appopriate mirrors if you enter your two letter country code.);

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic

# Ubuntu supported packages (packages)
deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://au.archive.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-updates universe multiverse

# Ubuntu community supported packages (sources)
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-updates universe multiverse

```

---

### Post by aysiu on 2005-11-15
See first link in my sig.

---

### Post by ubuntu_demon on 2005-11-16
mine is here :
[http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

---

### Post by ch13f121 on 2005-11-16
nevermind guys I got it thanks anyway, all it was was a # sign was taken out...

---

