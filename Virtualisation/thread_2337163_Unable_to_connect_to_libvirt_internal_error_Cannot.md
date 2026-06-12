---
title: "Unable to connect to libvirt internal error: Cannot find suitable emulator for x86_64"
date: 2016-09-15
forum: Virtualisation
---

### Post by gregor15 on 2016-09-15
Somehow, after updating to Kubuntu 16.04, KVM can not been started with error:

[B]Unable to connect to libvirt.
[/B]
internal error: Cannot find suitable emulator for x86_64

Libvirt URI is: qemu:///system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 977, in _open_thread
    self._populate_initial_state()
  File "/usr/share/virt-manager/virtManager/connection.py", line 939, in _populate_initial_state
    logging.debug("conn version=%s", self._backend.conn_version())
  File "/usr/share/virt-manager/virtinst/connection.py", line 316, in conn_version
    self._conn_version = self._libvirtconn.getVersion()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3889, in getVersion
    if ret == -1: raise libvirtError ('virConnectGetVersion() failed', conn=self)
libvirtError: internal error: Cannot find suitable emulator for x86_64


I was originally trying to reinstall KVM with this Wiki:
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

but was stuckt in a step 
```
rmmod kvm
rmmod: ERROR: Module kvm is in use by: kvm_intel

```

Here are output of lsmod | grep kvm

```
lsmod | grep kvm
kvm_intel             172032  0
kvm                   540672  1 kvm_intel
irqbypass              16384  1 kvm

```

I have found several quazi [SOLVED] forms but with no real solution.

Any help appreciated.  Thanks!

---

### Post by gregor15 on 2016-09-16
Solved by uninstalling everything, deleting files and folders and removing all related users and groups.

---

