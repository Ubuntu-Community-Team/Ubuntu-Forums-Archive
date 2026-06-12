---
title: "Java Problem"
date: 2007-12-30
forum: Sun Sparc Users
---

### Post by jose158 on 2007-12-30
I don't know if this is the right place to post,but oh well. I have tried to install Java for my firefox, but for some reason, I still can't play any java games!!! help.

---

### Post by papatrpt89 on 2007-12-30
How exactly did you go about installing java?

Anyways, there is a community maintained website, [http://www.ubuntuguide.org](http://www.ubuntuguide.org) that tells you how to install java.

Go to a command line, and try typing in:
```
sudo apt-get install sun-java6-plugin
```I'm not sure how familiar you are with the typical way of installing things in Ubuntu.  Google around for aptitude, apt-get, synaptic, and the like ;) you may like what you find!

---

### Post by AdNZL on 2007-12-31
I'm having exactly the same issue. Tried the imputing that line into the terminal, and I can't see anything that I've missed in the package manager, although there is  a lot of stuff in there. gonna keep looking.

---

### Post by jose158 on 2007-12-31
Ok, I fixed it. I got the problem solve from here: [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by papatrpt89 on 2007-12-31
Google FTW!

---

### Post by switlikbob on 2008-01-08
Nothing here is working for me...I tried to install the debian package, and that doesn't work either...I get an unexpected "(" when it tries to build the package form the binary.  When I try the old fashioned way, I get this:

$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by k8fox1 on 2008-01-16
I received this same error!

---

### Post by psychicist on 2008-01-20
This problem can't be marked as solved since there is no JDK 6 for Linux/SPARC, only for Solaris/SPARC. So if there are any developers here who are interested in getting it to work on Linux/SPARC, please let me know. I don't run Ubuntu but I'm running Linux on SPARC so we could collaborate on getting OpenJDK/IcedTea working on this architecture.

The person who claims to have solved this problem has either installed x86 binaries which won't work or installed the older, unsupported and insecure Java Blackdown 1.4.2_01 for Linux/SPARC, which is not a good thing to do if you're connected to the internet.

---

