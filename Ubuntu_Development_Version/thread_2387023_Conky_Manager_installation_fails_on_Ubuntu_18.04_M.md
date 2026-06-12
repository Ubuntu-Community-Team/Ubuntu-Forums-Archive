---
title: "Conky Manager installation fails on Ubuntu 18.04 MATE (Bionic)"
date: 2018-03-13
forum: Ubuntu Development Version
---

### Post by wtowbin on 2018-03-13
When trying to install Conky Manager via
 dpkg -i conky-manager-v2.4-amd64.deb

I am getting "Dependency is not satisfiable: realpath"

Any idea ho to fix this ?

Thx, Walter

---

### Post by QIII on 2018-03-13
Moved to Ubuntu Development version.  Bionic is not yet in production.

---

### Post by mc4man on 2018-03-13
The last time the realpath package actually contained anything usable (/usr/bin/realpath) was 14.04, since then it's been just a transitional package for coreutils
In 18.04 that package has finally been dropped. The person maintaining your package should adjust, they've had almost 5 years..
You could likely just install the 17.10 package, it's got basically nothing in it so no harm - 
[https://packages.ubuntu.com/artful/realpath](https://packages.ubuntu.com/artful/realpath)

---

### Post by wtowbin on 2018-03-13
Works .. Thank you.
W

---

### Post by mikeid on 2018-03-24
Thank-you!

---

### Post by howefield on 2018-05-11
Thread closed.

---

