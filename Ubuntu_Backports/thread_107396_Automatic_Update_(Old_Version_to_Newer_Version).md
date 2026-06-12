---
title: "Automatic Update (Old Version to Newer Version)"
date: 2005-12-22
forum: Ubuntu Backports
---

### Post by kenweill on 2005-12-22
Hi.
Is it possible to have an automatic update version to version?

I mean for example, Ubuntu 5.04 to 5.10 or to newer version.

Is that possible? Or do I have to download the latest version and install a new copy of it?

How?

---

### Post by ape on 2005-12-23
It is possible to completely upgrade your 5.04 system to 5.10.

You need to edit our /etc/apt/sources.list and change every reference of 'hoary' to 'breezy'.

Then do the following:

    apt-get update
    apt-get dist-upgrade

This should pull all the new breezy packages down.  Worked like a charm here..

---

### Post by imagine on 2005-12-23
Read [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade) and 
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

Don't forget to "apt-get install ubuntu-base ubuntu-desktop" after the dist-upgrade.
And be aware that apt-get does not know anything about applications which were installed without apt-get/dpkg (eg with make && make install), so those programs could cause problems.

---

