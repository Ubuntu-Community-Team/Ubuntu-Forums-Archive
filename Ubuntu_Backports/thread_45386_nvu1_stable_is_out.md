---
title: "nvu1 stable is out"
date: 2005-06-29
forum: Ubuntu Backports
---

### Post by ubuntufans on 2005-06-29
please pretty please :) backport nvu 1.0

---

### Post by sapo on 2005-06-29
hm.. i want it too  :grin:

---

### Post by benplaut on 2005-06-29
[QUOTE=sapo]hm.. i want it too  :grin:[/QUOTE]

 :)  me too!

---

### Post by benplaut on 2005-07-03
boomp?  \\:D/

---

### Post by ZephyrXero on 2005-07-06
I would love to have the new 1.0 Final version of Nvu too :)

---

### Post by jdong on 2005-07-07
I need it in Breezy/Universe first.

---

### Post by ZephyrXero on 2005-08-11
There's an [Nvu 1.0 Autopackage](http://autopackage.org/packages) available now  :grin: 

Works great on my machine ;)

---

### Post by AgenT on 2005-08-12
No need for that. Just download the rpm file from the official website and convert using alien.

What you want is this rpm file (there are multiple, this is the only one that seems to works):
nvu-1.0-1.rhel3.fs.i386.rpm

Then type in your console:
 ```
alien nvu-1.0-1.rhel3.fs.i386.rpm
```
This will convert the rpm to a deb. After it is done, type this to install:
 ```
sudo dpkg -i nvu_1.0-2_i386.deb
```

---

