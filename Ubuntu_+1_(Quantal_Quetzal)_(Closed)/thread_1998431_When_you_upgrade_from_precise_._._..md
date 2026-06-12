---
title: "When you upgrade from precise . . ."
date: 2012-06-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-06-06
don't forget about reporting your results to the isotracker (including bugs!). During the milestone testing (like alpha 1, alpha 2, etc) bugs reported this way even get extra attention from the applicable developers as during the milestone the archive and iso should be in a stable and working state.

Right now for alpha 1, the links are:

Upgrade i386 ubuntu
[http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16910/testcases/191/results](http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16910/testcases/191/results)

Upgrade amd64 ubuntu
[http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16909/testcases/192/results](http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16909/testcases/192/results)

And for you flavor folks, there are upgrade tests for you as well! Please report your results good or bad. All you need is a ubuntu SSO account to login.

---

### Post by kansasnoob on 2012-06-07
I tried Ubuntu and Lubuntu i386 and both failed:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1009857](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1009857)

---

### Post by jerrylamos on 2012-06-07
Before there were any quantal i386.iso I used apt.sources change precise>quantal and update/upgrade.  I saved everything then did a fresh install of precise, up to date, and then the update/upgrade.

When the i386.iso came out I've been doing new installs looking for bugs in startup disk creator, startup disks, and the resulting install.

However this activity is not "on topic" for this thread.  

"upgrading" for me invariably results in a larger disk image and may even fail.  Why do I care about disk image size??  I have several partitions with various levels of quantal, precise, lucid, even meerkat which I use to recover bugs.  Upgrading these images results in increasing size.  Yes I do apt-get remove, autoremove, synaptic to clean off old headers, ... still wind up with a disk image hundreds of thousands of bytes larger than a new install with the same packages.

So my bugs are noted in launchpad and other threads having more to do with installs and running quantal.

Jerry

---

