---
title: "Problems installing software"
date: 2015-05-02
forum: Software
---

### Post by joe165 on 2015-05-02
how to install software since l dont have athentication previledges

---

### Post by QIII on 2015-05-02
Hello!

What do you mean by not having authentication privileges?

---

### Post by kc1di on 2015-05-02
Hello joe165 and welcome to Ubuntu,

there are several ways to install software on Ubuntu.  you use your user password to gain administrative privileges. 
In the software center you'll be prompted for a password , simply enter your user password.
from a terminal you can use "sudo" to access administrative privileges for example
```
sudo apt-get install <package name>
``` you enter your user password when prompted.  and replace <package name> with the name of the package you want to install (Without the brackets)

[here's a page]("https://help.ubuntu.com/community/InstallingSoftware") about installing software you may want to read also.

---

