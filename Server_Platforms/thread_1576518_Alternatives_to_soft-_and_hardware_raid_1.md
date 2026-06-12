---
title: "Alternatives to soft- and hardware raid 1"
date: 2010-09-17
forum: Server Platforms
---

### Post by curan on 2010-09-17
Hi guys,

I am trying to make a NAS solution for our club, which should contain different data for download. I have been looking at freeNAS, openfiler and other solutions but they don't offer quite what i want.

I want data security, but trying to avoid software and hardware raid.
Windows Home Server has a function, where it copies the data from the 'main' storage disk and over to the 'backup' data storage drive automatically. 

I know it is bad explained, but does anybody know a solution for this?

---

### Post by BkkBonanza on 2010-09-17
On a simplistic level rsync is good at mirroring drives, easy to setup and fairly effcient at copying changed files. But it requires periodic scans and isn't continuous.

For a more advanced approach there is DRBD (Distributed Replicated Block Device) of which I know little except it exists and does block level mirroring across networks.

See here, for an overview. It looks very new,
[http://www.ibm.com/developerworks/linux/library/l-drbd/index.html?ca=dgr-lnxw97LX-DRBD](http://www.ibm.com/developerworks/linux/library/l-drbd/index.html?ca=dgr-lnxw97LX-DRBD)

There are DRBD utils in the [Ubuntu repos]("https://launchpad.net/ubuntu/+source/drbd8").

---

