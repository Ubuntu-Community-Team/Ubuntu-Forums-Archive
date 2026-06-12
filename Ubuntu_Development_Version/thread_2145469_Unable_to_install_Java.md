---
title: "Unable to install Java"
date: 2013-05-15
forum: Ubuntu Development Version
---

### Post by Curtis6767 on 2013-05-15
Used the same Webupd8 method as I've done many times before. Had trouble with the PPA, but got that installed, now just get an error message about not finding site when I try to get the java installer installed.

Anyone else?

---

### Post by jfernyhough on 2013-05-15
Just use OpenJDK. ;)

More seriously, it's possible that Oracle have moved the file or there's a new version. Or you've added the PPA without changing saucy to raring (at the moment, the only package for Saucy is Java 8). Or your network isn't resolving properly.

More information needed.

---

### Post by Curtis6767 on 2013-05-15
This is the error message I get:

Unable to locate package oracle-java7-installer

---

### Post by sammiev on 2013-05-15
Go into your source.list and change it to raring,

---

### Post by hendrel on 2013-05-16
Here is a step by step procedure to install Java 7 update 21. [http://hendrelouw73.wordpress.com/2013/05/07/how-to-install-oracle-java-7-update-21-on-ubuntu-13-04-linux/](http://hendrelouw73.wordpress.com/2013/05/07/how-to-install-oracle-java-7-update-21-on-ubuntu-13-04-linux/)

---

### Post by slickymaster on 2013-05-16
> **jfernyhough said:**
> J...Or you've added the PPA without changing saucy to raring (at the moment, the only package for Saucy is Java 8)...

> **sammiev said:**
> Go into your source.list and change it to raring,

+1
That's the simple and faster way to solve it.

Another way to deal with it, way more cumbersome, is to follow [this tutorial]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux").

---

