---
title: "Package repository differs between Ubuntu Server and Ubuntu Desktop"
date: 2007-08-08
forum: Server Platforms
---

### Post by kbman on 2007-08-08
Hi,

I've want to install 
libdbd-pgsql   0.7.1-3.1ubunt PostgreSQL database server driver for libdbi


Now both these packages are available for install on Kububtu, but when I want to install it on a Ubuntu Server, the package isn't there - only libdbd-mysql

I've compared the sources.list file for both machines and they are the same. Any ideas why the two differ ?

Thanks
Gerard

---

### Post by tgm4883 on 2007-08-08
because it's not in the server repo?

have you tried apt-get update first to be sure?

---

### Post by Seisen on 2007-08-08
There is no server repository or desktop repository it is the same thing. Make sure that you have the Universe Repository enabled because the package you want is in there.

---

### Post by tgm4883 on 2007-08-08
> **Seisen said:**
> There is no server repository or desktop repository it is the same thing. Make sure that you have the Universe Repository enabled because the package you want is in there.

There's no different repos for 32-bit vs 64-bit either but not all the packages are available in each other.

---

