---
title: "[SOLVED] sources.list problem"
date: 2008-07-27
forum: System76 Support
---

### Post by general vegitable on 2008-07-27
hi, i'm new here i got ubuntu this week, and i seem to have a problem with sources.list, i have this error:
```
E: Type ‘hardy’ is not known on line 2 in source list /etc/apt/

```
this happened after i typed into the terminal:
```
 sudo apt-get update

```

i have no idea what is wrong with my installation but i think that my sources.list is corrupt, is there a way to fix this error?

kindest regards 
             gv

---

### Post by Waappu on 2008-07-27
Hi

Type in terminal ```
gksudo gedit /etc/apt/sources.list
```to check your source list.

You can see default source list from this post
[http://ubuntuforums.org/showthread.php?t=739119](http://ubuntuforums.org/showthread.php?t=739119)

---

### Post by general vegitable on 2008-07-27
thanks, i tried it, and it works

---

