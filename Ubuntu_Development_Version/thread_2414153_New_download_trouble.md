---
title: "New download trouble"
date: 2019-03-06
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-03-06
I use synaptic to update/upgrade.
Since a dozen days i get some errors when i first try to upgrade, like today:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-x86-64-linux-gnu_2.32-5ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-x86-64-linux-gnu_2.32-5ubuntu1_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]
but this happen only with the first try: when validating again the upgrade, the packages are downloaded.

Wonder if that issue comes from apt or launchpad :confused:

---

### Post by SeijiSensei on 2019-03-06
I often change my source server to one nearby rather than use archive.ubuntu.com.  Universities are often a good bet since they have lots of bandwidth.  It's easiest to do this from within a graphical tool, but you can also edit /etc/apt/sources.list manually using sudo.

---

### Post by dino99 on 2019-03-06
I does not blame the sources themselves, but either the downloading tool/script: as firstly said, i have met that issues many times, and the scenario is always the same: first download test fails, but a few seconds later trying again, the download is done. So its likely not the servers being  too busy, but apt or launchpad or a timer lock that needs to be 'awaken'.

---

### Post by dino99 on 2019-03-23
That works better now; Seems a launchpad problem, pushing the files list too early in some cases, and the download still pending for some seconds/minutes.

---

