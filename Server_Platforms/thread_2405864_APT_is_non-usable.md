---
title: "APT is non-usable"
date: 2018-11-12
forum: Server Platforms
---

### Post by pixel2 on 2018-11-12
Just this.  No matter what I try to do with apt, console get spammed with some meaningless messages.E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening 
E: The package lists or status file could not be parsed or opened.

Huh? Provided file exist and is accesible .

---

### Post by kc1di on 2018-11-12
Try this command```
sudo apt update
``` post any error messages you get here:

---

### Post by deadflowr on 2018-11-12
What does 
```
ls /var/lib/dpkg
```
show?

---

