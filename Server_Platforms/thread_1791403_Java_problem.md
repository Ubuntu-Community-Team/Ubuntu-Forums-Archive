---
title: "Java problem"
date: 2011-06-26
forum: Server Platforms
---

### Post by tarciokk on 2011-06-26
Hi, I install ubuntu server amd64bit. And  configured everything  normal. Phpmyadmin, user, ftp, putty, internet,raid... perfect work!
 But no Java ... : (


 I'm trying to start L2 server, and I get this error.

 root @: / lineage / login #. / startLoginServer.sh
 Exception in thread "main" java.lang.NoClassDefFoundError: version
 Caused by: java.lang.ClassNotFoundException: version
         at java.net.URLClassLoader $ 1.run (URLClassLoader.java: 202)
         at java.security.AccessController.doPrivileged (Native Method)
         at java.net.URLClassLoader.findClass (URLClassLoader.java: 190)
         at java.lang.ClassLoader.loadClass (ClassLoader.java: 307)
         at sun.misc.Launcher $ AppClassLoader.loadClass (Launcher.java: 301)
         at java.lang.ClassLoader.loadClass (ClassLoader.java: 248)
 Could not find the main class: version. Program will exit.

 

 Java install by this tuturial  [http://www.how-to.lt/viewtopic.php?f=6&t=82](http://www.how-to.lt/viewtopic.php?f=6&t=82)
 ```
 apt-get install sun-java6-jdk 
```
 I later Tring
 ```
 apt-get install sun-java * 
``` ITS did not help.

 Maybe someone can help for my Resolve this problem? My Skype: rayne.lt or post your answer there, thanks!


 [SIZE=150] ** [COLOR=PaleTurquoise]Maybe I need first start  java ? or configure somewhere? [/COLOR]** [/SIZE]

---

### Post by papibe on 2011-06-27
The sun-java packages are not enable by default on a server. Edit this file:
```
$ sudo nano /etc/apt/sources.list
```
and uncomment the following line:
```
# deb http://archive.canonical.com/ubuntu lucid partner
```
So it looks like this:
```
deb http://archive.canonical.com/ubuntu lucid partner
```
Then save the file and update your repositories:
```
$ sudo apt-get update
```
After that all sun-java packages should be available. To search for them:
```
$ apt-cache search sun-java6
```
I believe you'll need at least to install the run time:
```
$ sudo apt-get install sun-java6-jre
```
Hope it helps.

---

