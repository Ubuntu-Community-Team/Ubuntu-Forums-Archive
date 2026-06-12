---
title: "Upgrade from 11.10 to 12.04 LTS Ubuntu Server"
date: 2013-10-21
forum: Server Platforms
---

### Post by luciano_rinetti on 2013-10-21
After a do-release-upgrade in my 11.10 server i try to do "apt-get update" but i get this error:

Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release.gpg
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates Release.gpg
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports Release.gpg
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release                         
E: GPG error: [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

After i lot of reading, my understand is that there was one o more bugs in the 12.04 that relates to the "apt-get update"
but i have not found a definitive answer or workaround that let me complete my installation.
Many thanks if you have any help.
This is the "sources.list" file:

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

---

