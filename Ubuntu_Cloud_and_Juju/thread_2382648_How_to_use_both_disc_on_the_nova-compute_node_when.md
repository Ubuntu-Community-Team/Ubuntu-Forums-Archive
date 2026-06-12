---
title: "How to use both disc on the nova-compute node when deploy openstack by maas and juju?"
date: 2018-01-16
forum: Ubuntu Cloud and Juju
---

### Post by vannguyen3 on 2018-01-16
Hello,
I using MAAS and JUJU to deploy my openstack
My nova-compute node have 2 disc /dev/sda and /dev/sdb but i see that JUJU only use /dev/sda even MAAS saw the node have 2 disk
Do we have anyway to 'tell' JUJUto using both disc as nova-compute resource?
Thanks and Regards
Van

---

### Post by blakehenderson2 on 2018-02-08
Whether JUJU uses the second disk is dependent upon the options you have in your bundle.  Typically the second disk is used by cinder or ceph, which are optional services- are you deploying them? if so, check options you are using with them.

---

