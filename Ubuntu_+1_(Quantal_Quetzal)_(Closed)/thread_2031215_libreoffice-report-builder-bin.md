---
title: "libreoffice-report-builder-bin"
date: 2012-07-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by buzzmandt on 2012-07-21
i have 2 comps running quantal, one is upgraded to quantal, one is a fresh install from a daily build

mine (the one that is an upgrade to quantal) has libreoffice and it runs just fine.

the other (from fresh install) cannot install libreoffice because of libreoffice-report-builder-bin.


is there a way to force the install to ignore libreoffice-report-builder-bin and just install it anyway?


```
sudo apt-get install libreoffice
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-report-builder-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

```

searching for libreoffice-report-builder-bin finds nothing:
```
buzzmandt@buzzmandt-1:~/Documents$ aptitude search libreoffice-report-builder-bin
buzzmandt@buzzmandt-1:~/Documents$                  

```

---

### Post by PaulW2U on 2012-07-21
See [http://ubuntuforums.org/showthread.php?t=2030053](http://ubuntuforums.org/showthread.php?t=2030053)

Problem already fixed. I downloaded from proposed a few hours ago.

---

### Post by arpanaut on 2012-07-21
[http://ubuntuforums.org/showpost.php?p=12120542&postcount=3](http://ubuntuforums.org/showpost.php?p=12120542&postcount=3)

Or should be fixed through normal channels soon.

---

### Post by buzzmandt on 2012-07-21
thanks

---

### Post by JMB74 on 2012-07-22
> **arpanaut said:**
> [http://ubuntuforums.org/showpost.php?p=12120542&postcount=3](http://ubuntuforums.org/showpost.php?p=12120542&postcount=3)

Or should be fixed through normal channels soon.

As it is.

[https://lists.ubuntu.com/archives/quantal-changes/2012-July/005254.html](https://lists.ubuntu.com/archives/quantal-changes/2012-July/005254.html)

---

