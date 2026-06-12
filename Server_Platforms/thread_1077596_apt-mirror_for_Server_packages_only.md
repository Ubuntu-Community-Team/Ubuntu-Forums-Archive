---
title: "apt-mirror for Server packages only"
date: 2009-02-22
forum: Server Platforms
---

### Post by auximini on 2009-02-22
Hello,

Is it possible to create an apt-mirror of only the packages Ubuntu Server uses? Considering the base server repository can fit on a CD and apt-mirror downloads 10-30gb of packages, I think that's a lot of wasted space.

Thanks
Joe

---

### Post by ikonia on 2009-02-22
the repo is the same in the server install - there are only specific packages such as the kernel (easy example) that are different. If you install mysql-server on a server install, it's the same package as mysql-server on a desktop install - hence the reason for home user kit, the desktop install makes an excellent choice for a home server over a server install.

---

### Post by auximini on 2009-02-22
Yep, I understand that the repos are the same. I was wondering if there was any way to limit the packages or mirror how the repo is set up on the CD. 

I tried copying the apt repo layout on the CD to an apt-mirror repository, but when I went to update apt-mirror, it overwrote all of the cd-specific settings.

---

