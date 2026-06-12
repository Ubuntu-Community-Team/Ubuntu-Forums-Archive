---
title: "Unable to create VM"
date: 2019-10-25
forum: Virtualisation
---

### Post by satimis on 2019-10-25
Hi all,

Ubuntu 18.04 desktop

It frustrates me that after spending an hour I couldn't create VM of VirtualBox.  Only Linux 32bit is available for selection.

I have tried
1)
Install VirtualBox on repo

2)
Install VirtualBox 6.0 according to;
How To Install VirtualBox 6.0 on Ubuntu 18.04 LTS
[https://tecadmin.net/install-virtualbox-on-ubuntu-18-04/](https://tecadmin.net/install-virtualbox-on-ubuntu-18-04/)

On host;
$ uname -i```

x86_64

```

This is my first time encountering such a funny problem in running VirturalBox

Please help.  Thank in advance.

Motherboard:
Asus PRIME X570-P

Regards
satimis

---

### Post by TheFu on 2019-10-25
Is vt-x enabled in the BIOS?   AMD calls it something else.   AMD-v?   Asus MBs use something like SVM.

Advanced &#8594; CPU Configuration &#8594; SVM.

---

### Post by satimis on 2019-10-25
> **TheFu said:**
> Is vt-x enabled in the BIOS?   AMD calls it something else.   AMD-v?   Asus MBs use something like SVM.

Advanced &#8594; CPU Configuration &#8594; SVM.
Hi,

You're right.  It names SVM.  Just enable it.  Unfortunately there is no explanation.

Lot of thanks for your help.

Regards
satimis

---

### Post by TheFu on 2019-10-25
Please help the community and mark the thread SOLVED, so others don't waste time.

---

