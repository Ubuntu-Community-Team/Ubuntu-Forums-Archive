---
title: "Downloading files instead of viewing in browser"
date: 2011-01-12
forum: Server Platforms
---

### Post by ebest97 on 2011-01-12
Hello. I am wondering why PHP files are downloading instead of viewed in the web browser. It's phpSysInfo to be exact. I got this fixed on Linux Mint but can't remember how I did it.

Thanks!

---

### Post by wongo888 on 2011-01-12
Did you install your app via:

```
$ sudo apt-get install phpsysinfo
```

Did you try:

```
$ sudo aptitude install php5 libapache2-mod-php5
```

Try to see if php5 is loading:

```
$ apache2ctl -M | grep php
 php5_module (shared)
Syntax OK

```

---

