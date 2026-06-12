---
title: "MAAS commissioning error no writable disks"
date: 2017-01-30
forum: Ubuntu Cloud and Juju
---

### Post by gspencer3 on 2017-01-30
Hey there,

I went to recommission our nodes and now I am getting this error across the board:
[error] NODE: Unable to set any default storage layout because it has no writable disks.

Any idea?

---

### Post by blakehenderson on 2017-02-01
Did you check your nodes to ensure the storage is configured-- on MAAS select the node and look under STORAGE-- you may have to select the drive and partition it.

---

### Post by gspencer3 on 2017-02-01
Unfortunately, you can only do that once the node has been commissioned... which happens, but can not find any writable disks! Anyways, I wiped / purged maas from the controller node and reinstalled.. now it works.

Bug report here: [https://bugs.launchpad.net/maas/+bug/1660495](https://bugs.launchpad.net/maas/+bug/1660495)
MAAS crew knows about it (through IRC) and hopefully they can use the provided logs to sort that out for future peoples.

---

