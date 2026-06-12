---
title: "linux-lowlatency metapackage to be removed by upgrade?"
date: 2017-03-16
forum: Ubuntu Studio
---

### Post by heldal2 on 2017-03-16
Current upgrades in line for Ubuntu Studio (16.10) suggest to remove the linux-lowlatency package. Have the dependencies handled by this package been moved elsewhere? I can not see any obvious target among the packages suggested for installation or upgrade (dist-upgrade).

These are the suggested changes:
```
Remove: 
  linux-lowlatency
Install: 
  linux-headers-4.8.0-42
  linux-headers-4.8.0-42-lowlatency
  linux-image-4.8.0-42-lowlatecy
  linux-tools-4.8.0-42
  linux-tools-4.8.0-42-lowlatency
Upgrade:
  libthunar-2-0
  linux-headers-lowlatency
  linux-libc-dev
  linux-libc-dev:i386
  linux-tools-common
  linux-tools-lowlatency
  thunar
  thunar-data
  
```
I have tried to change the package server from a local mirror to the main servers in case something hasn't been distributed properly and reloaded the package database, but that makes no difference. The update looks like a half-way switch from a lowlatency to a generic kernel, but the removed lowlatency-metapackage isn't replaced by its generic counterpart. Could it be that the latest build of the lowlatency-kernel is incomplete and shouldn't have been distributed yet? I'm holding back the update and keep checking the servers for further updates in the coming hours.

---

### Post by heldal2 on 2017-03-21
Solved: Probably an incomplete/inconsistent set of upgraded kernel-related packages submitted to the server. A complete set with all dependencies covered was distributed within a few hours.

---

