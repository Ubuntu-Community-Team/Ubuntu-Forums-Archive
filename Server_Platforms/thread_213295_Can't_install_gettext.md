---
title: "Can't install gettext"
date: 2006-07-11
forum: Server Platforms
---

### Post by sikke on 2006-07-11
Hi!

I'm installin gettext on my breezy server and after running apt-get install gettext I get depency error for libgcj6. So I try to install again with libgcj6 and get depency error for gcc-4.0-base and it says I should install gcc-base version 4.0.1-4ubuntu9 but 4.0.3-1ubuntu3 is marked as installed. How can I install the 4.0.1-4ubuntu9 package? Or should I even do that?

Thanks!

---

### Post by lamego on 2006-07-11
Please review your /etc/apt/source.list and make sure you have only the official ubuntu repositories for breezy.
Most of the times dependencie problems are caused by using 3rd party repositories which provide packages which are not compatible with the default ubuntu versions.

---

### Post by sikke on 2006-07-12
Hi!

My /etc/apt/sources.list looks like this:

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy-updates main restricted


 deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Everything ok?

---

### Post by sikke on 2006-07-12
I've been thinking if I could solve this with dist-upgrade but I'm afraid to do it since I can't be sure that nothing would be broken after the upgrade. Basically I'm running LAMP but it is based on PHP5, MySQL 5.0.x and also runs MapServer for my WMS so there are a bunch of packages compiled from source outside of the ubuntu repository.

---

### Post by sikke on 2006-07-14
*bump*

---

