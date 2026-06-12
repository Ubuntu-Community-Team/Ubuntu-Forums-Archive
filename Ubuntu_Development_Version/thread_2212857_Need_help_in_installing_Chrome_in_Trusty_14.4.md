---
title: "Need help in installing Chrome in Trusty 14.4"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by Clifford_Sarokoff on 2014-03-23
I've downloaded the deb for Chrome from Google and tried to install it.  I get a package error. I tried both the stable and beta versions without success.
Does anyone have a solution?
CliffordS

---

### Post by Mateusz Stachowski on 2014-03-23
Several users reported that Chrome can't be installed with Ubuntu Software Center that is this [bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228").

You can however install it with dpkg.

```
sudo dpkg -i deb package
```

---

### Post by Clifford_Sarokoff on 2014-03-23
Many thanks; I used GDebi package prohram and it was successful. 
CliffordS

---

