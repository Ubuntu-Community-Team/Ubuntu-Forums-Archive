---
title: "Dangling UDEV links after removing FC LUNs"
date: 2016-12-03
forum: Server Platforms
---

### Post by wondra on 2016-12-03
Also posted here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1647067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1647067)

We're using Q-Logic QLE2562 Fibre Channel adapters (qla2xxx driver)  against a HPE 3PAR 7400c storage array in an OpenStack environment. The  OpenStack 3PAR driver manages volume attachments from the array to the  servers. There is 4 path multipath to every volume.

As the LUNs are removed, sometimes udev does not remove all links,  particularly in /run/udev/links and /dev/disk/by-path. The symptoms are  multiple records in one by-path directory under /run/udev/links, broken  links to no longer attached luns in dev/disk/by-path and links between  wrong LUNs and scsi devices there. I'm getting "multipathd: udev trigger  error" in syslog.

OpenStack relies on these links. When another volume is attached using a  LUN that has these leftover links and it happens that it is the first  of the 4 paths, OpenStack incorrectly identifies the volume and attaches  the same volume to multiple instances, leading to data loss.

What could be causing this behavior?

Ubuntu version 14.04
Linux version Ubuntu 4.4.0-47.68~14.04.1-generic 4.4.24
udev 204-5ubuntu20.19

---

