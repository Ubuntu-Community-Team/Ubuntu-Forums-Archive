---
title: "[Request] Eclipse 3.1"
date: 2005-07-01
forum: Ubuntu Backports
---

### Post by at2000 on 2005-07-01
Hi,

Eclipse 3.1 has just been uploaded to breezy. Please consider packaging it. It seems to depend on the newest gcj-4.0 as well as a brunch of java libraries.

---

### Post by at2000 on 2005-07-01
I've successfully built eclipse-{ecj,efj,jdt,pde,platform,rcp,sdk,source} using the following packages from breezy:
* ecj-bootstrap 3.0.1-4ubuntu4
* java-common 0.22ubuntu2
* liblucene-java 1.4.3-5ubuntu1
* liblucene-java-doc 1.4.3-5ubuntu1
Other dependencies are already in ubp.

---

### Post by stoffe on 2005-07-05
Bump. I want to give Eclipse another shot, and it'd be great if it was possible to install this way! :)

---

### Post by Mlehliw on 2005-07-05
3.1 is great but do you really need to install it from source? I just grabbed the 100 meg tar file from eclipse.org and everything was precompiled.

---

### Post by at2000 on 2005-07-07
Eclipse 3.1 in Ubuntu is natively precompiled (.so files in addition to .jar files) so does not need a Java SDK to run and should run faster.

---

### Post by tzutolin on 2005-07-07
[QUOTE=at2000]Eclipse 3.1 in Ubuntu is natively precompiled (.so files in addition to .jar files) so does not need a Java SDK to run and should run faster.[/QUOTE]

This sounds great :) 

However, I tried breezy a few days ago, and it seems that there are still some bugs in it (e.g. the IDE will shutdown unexpectly).  :roll:

---

### Post by Hikaru79 on 2005-08-04
Eclipse 3.1 will be in Ubuntu Breezy? But, previous versions of Ubuntu have never carried Eclipse as far as I know, presumably for the same reason they didn't carry Java -- liscencing/legal issues. Has this changed? Will Eclipse 3.1 be part of the Ubuntu repositories? Will Java? (And when I say Java, I mean Sun's compiler, not gcj or blackdown or jikes)

Thanks :D

---

### Post by at2000 on 2005-08-06
Yes, Breezy will come with eclipse 3.1, in universe not multiverse. Time has changed and now free-java-sdk's can run a lot of applications. Eclipse is easier, because it uses swt, not swing.

---

