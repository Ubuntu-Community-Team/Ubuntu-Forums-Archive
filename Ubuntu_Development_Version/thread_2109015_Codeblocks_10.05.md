---
title: "Codeblocks 10.05"
date: 2013-01-26
forum: Ubuntu Development Version
---

### Post by alexalghisi on 2013-01-26
How do I install codeblocks 10.05 on Ubuntu 13.04 ? I've tried with " sudo apt-get install codeblocks " but this installs codeblocks 12.11

---

### Post by Toz on 2013-01-26
Moved to U+1 forum.

---

### Post by jbicha on 2013-01-26
Right, if you want to use 10.05 you'll need to use Ubuntu 12.04 LTS or 12.10:

[https://launchpad.net/ubuntu/+source/codeblocks](https://launchpad.net/ubuntu/+source/codeblocks)

---

### Post by alexalghisi on 2013-01-26
So no chance of using 10.05 on Ubuntu 13.04 ?

---

### Post by Kow on 2013-01-27
Don't hold me to this, but you could try installing the appropriate 10.05 deb for the most recent ubuntu release, which would be quantal.
[http://packages.ubuntu.com/quantal/codeblocks](http://packages.ubuntu.com/quantal/codeblocks) Scroll down a bit and you should find an amd64 and a i386 build. No promises, and this is definitely not supported.. but it may work.

EDIT: It could also break your system, but if you're using 13.04 at this point then I would expect you to expect breakage.
EDIT2: If it does work, you'll want to force version so ubuntu does not auto-upgrade it to the version in the raring repos.

---

