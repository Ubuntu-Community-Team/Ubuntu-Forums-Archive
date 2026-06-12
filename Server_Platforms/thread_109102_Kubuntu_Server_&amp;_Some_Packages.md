---
title: "Kubuntu Server &amp; Some Packages"
date: 2005-12-27
forum: Server Platforms
---

### Post by WebDev90 on 2005-12-27
Hi,

I have installed Kubuntu 5.1 but in server mode and I need some help.

1. How can I install "compat-libstdc++" on my server? I have already installed libstdc++5, libstdc++6 and libstdc++2.10- glibc2.2. I have suggestion as "rpm --query compat-libstdc++" but I do not want to install with this method. Any suggestion?

2. I need graphing support for a J2EE server. I do not installed X Windows libraries and I think I need some libraries. I need exuvalence of  "xorg-x11-deprecated-libs" on my server. But how?

3. How can I install "libmime-base64-perl" on my server. I could not find this package in my package archive.

My sources.list entries are as following:

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



Thanks in advance!

Cenk Eder

---

