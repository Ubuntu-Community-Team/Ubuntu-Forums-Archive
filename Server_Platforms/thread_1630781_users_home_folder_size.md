---
title: "users home folder size"
date: 2010-11-25
forum: Server Platforms
---

### Post by sipetron on 2010-11-25
please help
how can i increase my user's home folder size to 3Gb or more ??
of-course with using webmin

---

### Post by ajgreeny on 2010-11-25
I am totally baffled, and unable to answer your question as I don't understand exactly what the problem is.

Tell us more please; are you talking of a wubi install from within windows, or is this a partitioned install with too small a home partition.  I'm afraid your question does not make sense without us knowing more!

---

### Post by sipetron on 2010-11-25
i have ubuntu server using it as sharing server , i have have 24 user and i have 500 G hared disk but my problem is the users home folder size its 800Mb and i need to increase it and i dont know how

---

### Post by sanderd17 on 2010-11-25
if you can ssh to the server, you can use the parted program. Gparted is only a gnome frontend to parted. Do backup your data before you use parted.

---

### Post by James78 on 2010-11-25
It sounds like your system (Webmin) is setup to limit users total used memory, a.k.a. quota. Look around Webmin for how to change the Quota, perhaps the templates, plans, etc.

---

### Post by sipetron on 2010-11-25
its worked !!!!
i just enable the quota in the file system
thnks guys

---

