---
title: "Dahdi fails to install on ubuntu 9.10"
date: 2010-03-03
forum: Server Platforms
---

### Post by dexter4000 on 2010-03-03
Does anyone knows about this problem ? Everything installs fine but dahdi gives this error when thry to "make" .

root@ubuntu:~/dahdi-linux-2.2.1# make
make -C drivers/dahdi/firmware firmware-loaders
make[1]: Entering directory `/root/dahdi-linux-2.2.1/drivers/dahdi/firmware'
make[1]: Leaving directory `/root/dahdi-linux-2.2.1/drivers/dahdi/firmware'
You do not appear to have the sources for the 2.6.31-19-server kernel installed.
make: *** [modules] Error 1


Please help.

---

### Post by ICEB3AR on 2010-03-03
Ubuntu Karmic comes with:
> kernel-image-2.6.31-14

As it seems Dahdi needs 2.6.31-19 Maybe an older version of Dahdi does not need this new Kernel version.

---

### Post by dexter4000 on 2010-03-03
i do have the 2.6.31-19-server kernel sources installed but seems that dahdi wont detect them.

---

