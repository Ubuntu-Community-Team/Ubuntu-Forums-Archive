---
title: "Really need some help: E: Could not perform immediate configuration on 'libattr1'"
date: 2012-02-02
forum: Server Platforms
---

### Post by BarryDocks on 2012-02-02
I had a crash while doing a routine package upgrade (power outage), not I get the following error when I try to install any thing: 
```
E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```
Tried, 
```
apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
```
apt-get install libattr1
E: Could not perform immediate configuration on 'libselinux1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```
```
apt-get install libselinux1
E: Could not perform immediate configuration on 'libselinux1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```
```
apt-get autoremove --purge  libattr1                         Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libattr1 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
```
apt-get autoremove --purge libselinux1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libselinux1 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Really running out of options](*,)

---

