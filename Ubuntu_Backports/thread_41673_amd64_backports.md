---
title: "amd64 backports"
date: 2005-06-14
forum: Ubuntu Backports
---

### Post by daenney on 2005-06-14
Hey

Since i'm getting a new laptop with an AMD Turion64 and I will ofcourse run Ubuntu on it I was looking at the amd64 backports.
Couldn't help noticing that there is not a single app. backported for amd64. What's up with that, just failing mirros or not backporting anything for amd64?
If i wasn't all that new to Linux I'd help with compiling the apps from source...

---

### Post by man.life on 2005-06-14
You don't have to a developer or whatever to backport. And since you're getting an AMD64, you could contribute with your backports:

$ wget [ftp://ftp2.caliu.info/backports/projects/ubp-tools/ubp-build/ubp-build.py](ftp://ftp2.caliu.info/backports/projects/ubp-tools/ubp-build/ubp-build.py)
$ sudo gedit /etc/apt/sources.list

Add 

deb-src [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy main restricted universe multiverse

$ sudo apt-get update
$ ubp-build.py whatever

Once you are in the changelog, add ~5.04ubp1 to the version number and save it (Ctrl + o).

---

### Post by Mez on 2005-06-14
When things move over ot the Ubuntu Servers, the buildd will auto-backport them

---

