---
title: "vmware tools  Ubuntu 10.10  header files not found"
date: 2010-11-12
forum: Virtualisation
---

### Post by geohei on 2010-11-12
Hi.

When installing VMware Tools (VMware Workstation 6.5) on Ubuntu 10.10, I got the config error that the C header files matching the running kernel were not found.

Default location didn't exist:
/usr/src/linux/include

How can I resolve this?

Thanks,

---

### Post by gdahlm on 2010-11-13
Open up a terminal and run the following command

sudo apt-get install linux-headers-`uname -r`

---

