---
title: "Packages"
date: 2010-07-07
forum: Server Platforms
---

### Post by subba9000 on 2010-07-07
How to install Debian package for Ubuntu Server 10.04 ?

---

### Post by Yarui on 2010-07-07
Do you mean you have downloaded a .deb file and want to know how to use it?  You basically just run it and it installs the program, there isn't much to it.

---

### Post by Darkness Des on 2010-07-07
```
cd /dir/with/deb
sudo dpkg -i myprogram.deb
```

---

### Post by GreenN00b on 2010-07-07
There is an utility called gdebi for that. ```
gdebi filename.deb
``` should work.

---

### Post by arrrghhh on 2010-07-07
> **GreenN00b said:**
> There is an utility called gdebi for that. ```
gdebi filename.deb
``` should work.

I don't think that works without X.  Use the **dpkg** command referenced earlier.

---

