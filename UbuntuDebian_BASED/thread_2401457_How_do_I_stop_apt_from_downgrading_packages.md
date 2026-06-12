---
title: "How do I stop apt from downgrading packages?"
date: 2018-09-18
forum: Ubuntu/Debian BASED
---

### Post by nemanja2 on 2018-09-18
I've tried searching through various forums for a solution, but everyone seems to post that it's a good idea to downgrade packages installed.

Here's my problem with that. I'm using Deepin OS, have Viber, Mailspring and Skype installed, all downloaded from the official sites in .deb format, I've installed them, and now, running sudo apt-get update returns this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[B]The following packages will be DOWNGRADED:
  skypeforlinux viber mailspring [/B]
0 upgraded, 0 newly installed, 3 downgraded, 0 to remove and 0 not upgraded.

```
Now, I'm pretty new Linux user, how do I exclude them from downgrading? Apps stop working after the downgrade, since it installs deprecated versions.

---

### Post by deadflowr on 2018-09-18
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by nemanja2 on 2018-09-18
Damn, I'm an idiot.

So, if anyone wants to manually update the packages, just do:

```
 sudo apt-mark hold *name of the package* 
```

Reversing the changes:

```
 sudo apt-mark unhold *name of the package* 
```

---

