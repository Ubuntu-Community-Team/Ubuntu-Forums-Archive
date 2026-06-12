---
title: "Cinder (OpenStack Mitaka) and ZFS"
date: 2017-03-03
forum: Server Platforms
---

### Post by minimike2 on 2017-03-03
Hi there

I am buiding a new server for my SOHO office.

Ubuntu 16.04 on a ZFS Root
XEN Hypervisor
Percona 5.7 (Mysql)
OpenStack (Mitaka)
Gigabyte MB10-DS0 (Xeon D1541) with 128 GB Memory

From OpenStack Keystone, Nova, Glance, are running Neutron also but not tested. For Glance i need some informations :)

My System runs on ZFS. So  I havn't an LVM because I'm using ZFS.... What ist the best or better Ubuntu's way to get Cinder runnunig using ZFS?

I've found this [https://github.com/FransUrbo/Openstack-ZFS](https://github.com/FransUrbo/Openstack-ZFS)
But not sure if the described patch is now included inside ubuntu's zfsonlinux package

best regards
Darko

---

