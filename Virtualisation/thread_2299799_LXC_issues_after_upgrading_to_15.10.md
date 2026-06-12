---
title: "LXC issues after upgrading to 15.10"
date: 2015-10-21
forum: Virtualisation
---

### Post by enryfox on 2015-10-21
I've just Upgraded to Ubuntu 15.10 and I'm having problems with LXC container.

The distribution upgrade process failed while installing lxc but anything else installed fine; upon rebooting the desktop was up&running and I just removed and installed again all LXC packages (this time with no errors).

I'm trying to run a simple LXC container but I get the following errors:
```
lxc-execute: conf.c: tmp_proc_mount: 3503 No such file or directory - failed to mount /proc in the container.
lxc-execute: lsm/apparmor.c: apparmor_process_label_set: 183 No such file or directory - failed to change apparmor profile to lxc-container-default
lxc-execute: sync.c: __sync_wait: 51 invalid sequence number 1. expected 4
lxc-execute: start.c: __lxc_start: 1172 failed to spawn 'test_tcc101'
lxc-execute: cgmanager.c: cgm_remove_cgroup: 523 call to cgmanager_remove_sync failed: invalid request
lxc-execute: cgmanager.c: cgm_remove_cgroup: 525 Error removing all:lxc/test_tcc101-5
```

the lxc conf file is as follows:

```
lxc.utsname = test_tcc101
lxc.autodev = 0
lxc.network.type = veth
lxc.network.flags = up
lxc.network.name = eth0
lxc.network.link = br0 
lxc.network.veth.pair = tcc101veth
lxc.network.hwaddr = 0E:67:AD:8A:01:65
lxc.network.ipv4 = 10.10.1.101/16
```

with ubuntu 15.04 everything was working fine.

any idea of what might be wrong ?

thanks

---

### Post by enryfox on 2015-10-23
[Update] adding the line

```
lxc.aa_profile = unconfined
```

to my container configuration allows to create and execute the container; i still get a bunch of errors:

```
lxc-execute: conf.c: tmp_proc_mount: 3503 No such file or directory - failed to mount /proc in the container.
lxc-execute: lsm/apparmor.c: apparmor_process_label_get: 97 No such file or directory - opening /proc/1/attr/current

```

but, at least in my case, they do not appear to cause trouble to the binary i have to run.
Still looking for a way to fix those issues, anyway ....

bye
Enrico

---

