---
title: "Unable to change screen resolution"
date: 2018-03-19
forum: Virtualisation
---

### Post by satimis on 2018-03-19
Hi all

KVM
Host - Ubuntu 16.04 desktop
Guest - Ubuntu 16.04.4 desktop

Unable to change screen resolution on Guest.  Changing to other resolution always drops back to 1024x768.

Display resolution; 2560x1440

Please help.  This version, Ubuntu 16.04.4 desktop, seems having problem running on Virtualbox and KVM

Regards
satimis

---

### Post by satimis on 2018-03-19
Hi all,

The problem is in a new HWE kernel in ubuntu 16.04 (4.13).

Problem solved after running following commands:
```

sudo apt-get install linux-generic-lts-xenial
sudo apt-get purge linux-image-4.13*

```

Now I can change screen resolution.

Thanks

satimis

---

