---
title: "Force NX Free to use user ssh keys"
date: 2010-04-16
forum: Security
---

### Post by rozbarwinek on 2010-04-16
Hi

I have installed Free NX and SSH, configure it and running.

Now I want to make Free NX use my RSA keys.

I was using password authentication before, but I want to try keys authentication :)

I run:sudo dpkg-reconfigure freenx

but an error appears saying that "package freenx is not installed"

But I have installed 3 packages from NoMachine website :)

What's the problem?

---

### Post by cariboo on 2010-04-16
If the packages you installed weren't .debs, then dpkg isn't going to work. Have a look at [this]("https://help.ubuntu.com/community/FreeNX"), it may help.

---

### Post by rozbarwinek on 2010-04-16
> **cariboo907 said:**
> If the packages you installed weren't .debs, then dpkg isn't going to work. Have a look at [this]("https://help.ubuntu.com/community/FreeNX"), it may help.

They were deb's :)

---

