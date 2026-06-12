---
title: "[SOLVED] Java version hell"
date: 2008-04-12
forum: Server Platforms
---

### Post by CRCarl on 2008-04-12
All - 
 I am working on getting Tomcat running. I need to install sun-j2re1.5 I run - 

```
user@c2personal:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate

```

Here is my etc/apt/sources.list -
```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main
deb-src http://archive.canonical.com/ubuntu feisty-commercial main

```

Ideas?

---

### Post by CRCarl on 2008-04-12
OK, so tried something different - 

```
user@c2personal:$ sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-jdk 

```

That worked, BUT - 
```
shrike@c2personal:$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

```

Where is the new version!?!?!

---

### Post by CRCarl on 2008-04-12
Solved - 

```
sudo update-java-alternatives -s java-6-sun
```

---

