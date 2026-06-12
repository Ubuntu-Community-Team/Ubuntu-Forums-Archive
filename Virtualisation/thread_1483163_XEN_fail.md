---
title: "XEN fail?"
date: 2010-05-14
forum: Virtualisation
---

### Post by jonsjo on 2010-05-14
Hi all,

I've just installed ububtu 10.04 server LTS and trying to get XEN up 'n running.

The first thing i did was an install:
```
:~# sudo aptitude install ubuntu-xen-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  ubuntu-xen-server
The following NEW packages will be installed:
  python-dev{a} python-xen-3.3 python2.6-dev{a} xen-docs-3.3 xen-hypervisor-3.3 xen-utils-3.3
0 packages upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
Need to get 6,596kB of archives. After unpacking 20.8MB will be used.
The following packages have unmet dependencies:
  ubuntu-xen-server: Depends: xen-tools which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
ubuntu-xen-server [Not Installed]

Leave the following dependencies unresolved:
xen-utils-3.3 recommends libc6-xen
Score is -10081

Accept this solution? [Y/n/q/?]

```


ubuntu-xen-server Broken? Does anyone have any idea on howto fix?

Thanks,
 -- Jon

---

### Post by TheFu on 2010-05-14
Bad news dude.  Xen support as a Dom0 isn't part of 10.04.

You can see this (really the lack of it) in the list of changes in 10.04 here: [https://help.ubuntu.com/community/Server/TechSpecs/1004LTS](https://help.ubuntu.com/community/Server/TechSpecs/1004LTS)  Look under "Virtualization."

8.04 LTS with Xen will be supported for some time, so you can still do some planning. Xen using normal depots is over.  Redhad made a similar decision.

There are alternative methods to run Xen, but they will required more work and you'll be leaving the Ubuntu depot fold. Good luck to you (and me).

---

