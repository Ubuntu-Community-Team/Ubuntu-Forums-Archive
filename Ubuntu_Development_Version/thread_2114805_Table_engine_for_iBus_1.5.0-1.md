---
title: "Table engine for iBus 1.5.0-1"
date: 2013-02-11
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2013-02-11
This package have some problems.
Is only me ?

```
Changes for ibus-table versions:
Installed version: 1.4.99.20121012-1
Available version: 1.5.0-1

Version 1.5.0-1: 

  * New upstream release.
  * debian/control:
    - DMUA: removed
    - Uploaders: removed LI, added Yunqiang and me.
    - Std-ver: 3.9.3 -> 3.9.4, no change.
    - Dependencies: updated.
  * debian/rules:
    - Call dh_install with --fail-missing
```

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ibus-table
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.



sudo apt-get install ibus-table
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ibus-table : Depends: ibus (>= 1.5.0)
E: Unable to correct problems, you have held broken packages.




sudo apt-get install ibus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ibus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by dino99 on 2013-02-11
it need ibus >=1.5, but RR still only have 1.4.2; thats it (look at package properties into synaptic)
so you need to use ibus-table-xxxxxx 1.4.0 (and report a bug about ibus-table 1.5)

---

### Post by VinDSL on 2013-02-11
> **dino99 said:**
> it need ibus >=1.5, but RR still only have 1.4.2
True!

ibus-table 1.5.x is languishing in 'proposed', waiting for ibus 1.5.x.

One needs to be very careful with 'proposed' packages, these days. 

Actually, most of them shouldn't be installed by users.  It's more of a "heads-up" for devs. ;)

---

