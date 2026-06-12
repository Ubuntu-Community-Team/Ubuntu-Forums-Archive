---
title: "tried installing pending 03-22-24 1 problem"
date: 2024-03-22
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2024-03-22
how do I fix this

> N: Ignoring file 'ubuntu.sources.curtin.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Henry

PS Do I just delete it.

---

### Post by Claus7 on 2024-03-22
Hello,

under /etc/apt/sources.list.d/ I cannot find any file named curtin. I would try to:
sudo cp ubuntu.sources.curtin.old ubuntu.sources.curtin.oldbup

and see what I will get.

Regards!

---

### Post by Hewjr100 on 2024-03-22
I deleted it and updates is back to normal.

Gort

---

### Post by corradoventu on 2024-03-23
For the "File 'ubuntu.sources.curtin.old' in '/etc/apt/sources.list.d/" i opened a bug: [https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058811](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058811)

---

### Post by Doug S on 2024-03-23
I got the same with the ISO from 2024.03.22 and 2024.03.23. I chimed in on corradoventu's bug report.

---

