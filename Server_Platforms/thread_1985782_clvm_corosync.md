---
title: "clvm corosync"
date: 2012-05-23
forum: Server Platforms
---

### Post by pdrobe on 2012-05-23
I install ubuntu 12.04, clvm and corosync, but I have one problem when try to start clvmd with corosync. The command is:

clvmd -d2 -T20 -Icorosync
the output is:

clvmd could not connect to cluster manager
Consult syslog for more information
With strace is:

connect(3, {sa_family=AF_FILE, path="/var/run/lvm/clvmd.sock"}, 110) = -1 
ECONNREFUSED (Connection refused)
the path /var/run/lvm/ is correct.

Thanks for help.

---

### Post by pdrobe on 2012-05-24
Hi,

Please I need help for this item.

---

### Post by pdrobe on 2012-05-24
I installed these packages: pacemaker, clvm, corosync.
If I want to use clvmd with corosync (clvmd -T20 -Icorosync), then I need install openais package or not?

Thanks

---

### Post by raja.genupula on 2012-05-24
don't post so early , 24 hours minimum time needed between a BUMP of thread .

---

### Post by pdrobe on 2012-05-25
I install openais and set COROSYNC_DEFAULT_CONFIG_IFACE="openaisserviceenableexperimental:corosync_parser"

When I run clvmd -T20 -d2 -Iopenais
clvm start and its load with openais

but when I run clvmd -T20 -d2 -Icorosync
clvm not start.

Why CLVM not start with corosync.?

---

