---
title: "Request: yada-0.48"
date: 2005-12-18
forum: Requests
---

### Post by pef on 2005-12-18
Hello,

Please backport yada-0.48 to fix a bug in phpmyadmin (yada prerm generated script is buggy), so phpmyadmin cannot be removed cleanly.

[https://launchpad.net/distros/ubuntu/+source/phpmyadmin/+bug/5904]("https://launchpad.net/distros/ubuntu/+source/phpmyadmin/+bug/5904")

The fix was introduced in 0.44:

```
     [yada]("http://packages.debian.org/src:yada")      (0.44)     unstable;     urgency=medium 

      * Generate debconf header for preinst and prerm scripts.

  -- Piotr Roszatycki  <[dexter@debian.org]("http://qa.debian.org/developer.php?login=dexter@debian.org")>  Tue, 13 Sep 2005 23:19:12 +0200
``` 
 

 I've build yada-0.48 using pbuilder, builds fine and is installable, and phpmyadmin build using this version works fine.

Thank you

---

