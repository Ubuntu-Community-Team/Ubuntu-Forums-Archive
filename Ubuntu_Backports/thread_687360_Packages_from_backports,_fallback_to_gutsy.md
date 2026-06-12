---
title: "Packages from backports, fallback to gutsy"
date: 2008-02-04
forum: Ubuntu Backports
---

### Post by Impaque on 2008-02-04
Hello,

I was just wondering how would I set up that all packages are pulled from backports, if they exist there. If they don't, they get pulled from Gutsy repository.

Wiki doesn't specify that (in other words, it doesn't work) and in Debian it works like this (copypaste from my blog):

--- 8< ---

_Add to /etc/apt/sources.list:_
deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free

_Add to /etc/apt/preferences:_
Package: *
Pin: release a=etch-backports
Pin-Priority: 750
Package: *
Pin: release a=stable
Pin-Priority: 700

_Add to /etc/apt/apt.conf.d/00Cache:_
APT::Cache-Limit "33554432";
APT::Default-Release "etch-backports";

_Do:_
apt-get update
apt-get dist-upgrade

--- 8< ---

Doing the same in Gutsy (with different repository names, of course) doesn't work, because the updates are not getting fetched and installed. Can somebody give me a hint how can this be done?

Thanks!

---

