---
title: "What is the best practice for adding nameservers - minimal install"
date: 2015-10-12
forum: Server Platforms
---

### Post by bigorno on 2015-10-12
Hi,

As you may know it is possible to add the nameservers in dns-namerservers in /etc/network/interfaces or in /etc/resolv.conf

For minimal install, what should be the best practice? 

Is it installing resolvconf and adding dns-nameservers to /etc/networking/interfaces?

Is it adding the nameservers manually to /etc/resolv.conf?


What is your opinion about that?

thank you

---

### Post by Habitual on 2015-10-12
Most folks use /etc/resolv.conf I believe.
I know I do.
Manually.

---

### Post by SeijiSensei on 2015-10-12
See [http://ubuntuforums.org/showthread.php?t=2298476&p=13371779&viewfull=1#post13371779](http://ubuntuforums.org/showthread.php?t=2298476&p=13371779&viewfull=1#post13371779)

---

