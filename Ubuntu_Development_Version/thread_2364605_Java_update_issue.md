---
title: "Java update issue?"
date: 2017-06-25
forum: Ubuntu Development Version
---

### Post by DougieFresh4U on 2017-06-25
Wondering if there is an issue with Java/JDK as I am getting 
this while updating:
```
Setting up oracle-java9-installer (9b174-1~webupd8~0) ...
Using wget settings from /var/cache/oracle-jdk9-installer/wgetrc
Downloading Oracle Java 9...
--2017-06-25 11:26:38--  http://download.java.net/java/jdk9/archive/174/binaries/jdk-9-ea+174_linux-x64_bin.tar.gz
Resolving download.java.net (download.java.net)... 23.63.227.177, 23.63.227.139
Connecting to download.java.net (download.java.net)|23.63.227.177|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-06-25 11:26:39 ERROR 404: Not Found.

download failed
Oracle JDK 9 is NOT installed.
dpkg: error processing package oracle-java9-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java9-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QIII on 2017-06-25
What command are you issuing to update Java?

---

### Post by mc4man on 2017-06-25
The ppa needs to update it's packages to reflect new links, i.e. it would now be 
[http://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz](http://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz)
ect...
Forum truncates displayed link, diff is
://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz

---

### Post by DougieFresh4U on 2017-06-26
> **QIII said:**
> What command are you issuing to update Java?

Using the terminal to do usual updates but it's not completing 400+ updates 
due to java issue.
I've gone to Synaptic and marked all updates and apply but get the result with java issue.
Was kind of hoping someone had some 'sudo' magic for me as I'm no guru. :(

---

### Post by dino99 on 2017-06-26
with synaptic, you might be able to update 'step by step' instead of selecting the whole list. Sometimes the transition is not well managed; and the 'circular' dependencies on some packages can 'at some point' lock the upgrade. So the solution is to first upgrade the package(s) which does not conflict, and also use 'gtkorphan' to purge some old used packages and their settings which probably disturb the transitional process .

---

### Post by DougieFresh4U on 2017-06-26
> **dino99 said:**
> with synaptic, you might be able to update 'step by step' instead of selecting the whole list. Sometimes the transition is not well managed; and the 'circular' dependencies on some packages can 'at some point' lock the upgrade. So the solution is to first upgrade the package(s) which does not conflict, and also use 'gtkorphan' to purge some old used packages and their settings which probably disturb the transitional process .

Thank you, had forgotten about locking package in Synaptic.
Was able to complete updates once I locked up that Java mess!

---

### Post by mc4man on 2017-06-26
> **mc4man said:**
> The ppa needs to update it's packages to reflect new links, i.e. it would now be 
[http://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz](http://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz)
ect...
Forum truncates displayed link, diff is
://download.java.net/java/jdk9/archive/175/binaries/jdk-9+175_linux-x86_bin.tar.gz

And the ppa updated the builds this morning to the 175 version...

---

### Post by DougieFresh4U on 2017-06-27
> **mc4man said:**
> And the ppa updated the builds this morning to the 175 version...
I should be a little more patient, after all this is the 'Development version'. :p
Thanks

---

### Post by henke54 on 2017-06-27
Here is (for me) a good site -> [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)
;)

---

### Post by QIII on 2017-06-27
By far, [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") is the best way to handle installing Oracle Java and keeping it updated.  You can install Oracle Java 9 by installing oracle-java9-installer instead.

Andrei is a one man show now and has been for several years.  Sometimes he misses something for a day or two.  But he will very quickly update his scripts.

---

### Post by DougieFresh4U on 2017-06-28
> **QIII said:**
> By far, [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") is the best way to handle installing Oracle Java and keeping it updated.  You can install Oracle Java 9 by installing oracle-java9-installer instead.

Andrei is a one man show now and has been for several years.  Sometimes he misses something for a day or two.  But he will very quickly update his scripts.

I have that ppa and as you said - Sometimes he misses something for a day or two.

---

### Post by slickymaster on 2017-06-28
> **DougieFresh4U said:**
> I have that ppa and as you said - Sometimes he misses something for a day or two.

Well, it's like QIII said. That PPA is maintained by a single person and sometimes he misses something for a day or two, but he's always quick updating it.

---

