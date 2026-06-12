---
title: "Enabling NFS4 in Ubuntu JeOS 8.04"
date: 2009-04-13
forum: Server Platforms
---

### Post by Dragonmantank on 2009-04-13
Is there a way to enable this, or am I just stuck until 9.04? I set up a few servers planning on using NFS4 but got bitten by this oversite in the -virtual kernal.

---

### Post by Dragonmantank on 2009-04-15
Bump?

---

### Post by nquinnathome1 on 2009-04-16
Have you tried the steps detailed here: [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) ?

---

### Post by Dragonmantank on 2009-04-16
Yes (which will be a separate thread here in a minute), but there is a bug in JeOS where the kernel wasn't built with NFS4 support like all the other kernels:

[https://bugs.launchpad.net/ubuntu-jeos/+bug/224138](https://bugs.launchpad.net/ubuntu-jeos/+bug/224138)

It's labeled as being fixed but I was unable to get it to work at all, so I just rebuild the servers as Ubuntu Server instead of JeOS.

---

