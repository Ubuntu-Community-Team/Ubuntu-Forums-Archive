---
title: "Smeg to be REMOVED from backports"
date: 2005-05-25
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-25
The extra gnome-menu libraries Smeg requires currently breaks the dependencies for gnome-devel, which is unacceptable to so many Ubuntu users.
 
 
As a result, I'll have to remove Smeg from Backports repositories until Amaranth can resolve this issue.
 
I will post downgrade instructions for the gnome libs soon (not at a Linux machine right now). If you think you know how, feel free to post them.

---

### Post by ow50 on 2005-05-25
This should work for downgrading
```
sudo apt-get install gnome-menus/hoary libgnome-menu0/hoary python-xdg/hoary
```
It will also remove smeg.

---

### Post by jdong on 2005-05-25
Thanks. I've confirmed these instructions are **correct**.

---

