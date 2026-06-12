---
title: "broken package indexes of  hoary-security/universe and hoary/universe"
date: 2005-07-20
forum: Repositories &amp; Backports
---

### Post by zwz on 2005-07-20
I started to experience this problem this morning.
# aptitude update
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [27.2kB]
99% [2 Packages gzip 0] [Connecting to cn.archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Sub-process gzip returned an error code (1)
Get:3 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/main Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/restricted Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/restricted Sources
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Packages
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/multiverse Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary-updates/restricted Sources
Get:5 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Packages [2853kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Packages
  Sub-process gzip returned an error code (1)
Get:6 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Sources [1142kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hoary/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 1m17s (0B/s)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

---

### Post by zwz on 2005-07-27
It turned out to be the infamous content-filtering Great Firewall of my country which broke the downloads of the package indexes. Sorry for the noise.

---

