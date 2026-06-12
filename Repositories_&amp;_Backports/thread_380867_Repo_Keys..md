---
title: "Repo Keys."
date: 2007-03-10
forum: Repositories &amp; Backports
---

### Post by Ezra on 2007-03-10
I'm using Kubuntu 6.10 and I made a directory in /usr/src/ for application source code, I used root to try and get the sources to kubuntu-desktop and ubuntu-desktop but it came back with an error:
```
root@Liquid:/usr/src/apps# sudo apt-get source ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Need to get 20.9kB of source archives.
Get:1 http://gb.archive.ubuntu.com edgy/main ubuntu-meta 1.30 (dsc) [558B]
Get:2 http://gb.archive.ubuntu.com edgy/main ubuntu-meta 1.30 (tar) [20.4kB]
Fetched 20.9kB in 0s (68.8kB/s)
gpg: Signature made Thu 19 Oct 2006 05:56:51 PM BST using DSA key ID 0F932C9C
gpg: Can't check signature: public key not found
dpkg-source: extracting ubuntu-meta in ubuntu-meta-1.30
dpkg-source: unpacking ubuntu-meta_1.30.tar.gz
root@Liquid:/usr/src/apps#
```
I get the same on "apt-get source kubuntu-desktop", how do I get the keys it wants and is that the only problem?

Help would be very much appreciated thanks.

---

### Post by Kateikyoushi on 2007-03-10
Try to run these in terminal.

```
gpg --keyserver subkeys.pgp.net --recv 0F932C9C
gpg --export --armor 0F932C9C | sudo apt-key add -
```

---

