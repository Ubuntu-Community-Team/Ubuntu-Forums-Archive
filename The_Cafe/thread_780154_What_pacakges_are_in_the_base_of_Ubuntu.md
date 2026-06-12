---
title: "What pacakges are in the base of Ubuntu?"
date: 2008-05-03
forum: The Cafe
---

### Post by tdrusk on 2008-05-03
I know that Ubuntu includes more packages as a base install than Debian. What packages are included. Is there a list somewhere?

---

### Post by scragar on 2008-05-03
[http://packages.ubuntu.com/hardy/ubuntu-desktop](http://packages.ubuntu.com/hardy/ubuntu-desktop) <-- check dependencies list.

---

### Post by LaRoza on 2008-05-03
> **tdrusk said:**
> I know that Ubuntu includes more packages as a base install than Debian. What packages are included. Is there a list somewhere?

[http://packages.ubuntu.com/hardy/base/](http://packages.ubuntu.com/hardy/base/)

(Note exactly sure. I have installed Debian and Ubuntu, and I noticed no major differences in packages)

---

### Post by capink on 2008-05-03
You can get a list using the following series of commands:

```
sudo apt-get install debootstrap
```

```
mkdir temp
```

```
debootstrap --print-debs hardy temp
```


Replace hardy with the distro you want. e.g etch


Edit: In addition to the list you get, you have to add a metapackage called linux-generic

---

### Post by bobbocanfly on 2008-05-03
```
wget http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz && zcat Sources.gz | grep Package: && rm Sources.gz
```

Everything in 'main' (that comes on the CD)

---

### Post by UbuWu on 2008-05-03
Here are the lists from which the official cd's are generated:
[http://people.ubuntu.com/~ubuntu-archive/seeds/](http://people.ubuntu.com/~ubuntu-archive/seeds/)

---

