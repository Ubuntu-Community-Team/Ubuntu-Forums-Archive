---
title: "ca't connect to hypervisor, connection reset by peer"
date: 2012-11-19
forum: Virtualisation
---

### Post by xtech on 2012-11-19
virsh -c qemu:///system list command gives me
error: Cannot recv data: Connection reset by peer
error: failed to connect to the hypervisor

syslog:
Nov 19 16:07:55 srv kernel: [ 2590.632213] init: libvirt-bin main process ended, respawning
Nov 19 16:07:56 srv kernel: [ 2591.572376] init: libvirt-bin main process ended, respawning

libvirtd.log
2012-11-19 14:09:02.211+0000: 23762: error : virGetGroupID:2265 : Failed to find group record for name 'oneadmin': Success
2012-11-19 14:09:02.211+0000: 23762: error : virStateInitialize:854 : Initialization of QEMU state driver failed

I'm running Ubuntu 12.04LTS and  libvirt version: 0.9.8.
Any pointers?

---

