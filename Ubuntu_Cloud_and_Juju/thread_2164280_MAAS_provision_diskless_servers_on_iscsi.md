---
title: "MAAS provision diskless servers on iscsi"
date: 2013-07-31
forum: Ubuntu Cloud and Juju
---

### Post by azpekt on 2013-07-31
Hi,

I`m using MAAS on Ubuntu 13.04, running as KVM guest in another Ubuntu 13.04 instance.

Our target is to provision diskless servers, that`ll have it`s root/swap filesystem mounted from RBD on Ceph. I can install such server manually (running into [this]("https://bugs.launchpad.net/ubuntu/+source/partman-iscsi/+bug/1047998") particular bug, however).

When I try to install Ubuntu via MAAS on such a server, it ends up in endless loop of "Starting up the partitioner" stage, jumping from 0% to 16% then 24% and back. Left it overnight, in a hope that this will sourt out itself. It hadn`t.

So, my question is - can I explicitly tell MAAS, that this server should pick up particular iqn from particular target, and install Ubuntu on it? Maybe, in pre-seed file somehow?

Thanks!

PS - and, if anyone will help me to fix that bug with iSCSI I mentioned - I`ll buy him a beer :)

---

