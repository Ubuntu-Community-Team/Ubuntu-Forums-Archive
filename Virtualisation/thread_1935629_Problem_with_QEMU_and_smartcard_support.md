---
title: "Problem with QEMU and smartcard support"
date: 2012-03-04
forum: Virtualisation
---

### Post by Onekiss on 2012-03-04
I have integrated smartcard reader:

```
root@8440p:/etc/libvirt/qemu# lspci
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
```I need to use it in guest operating system in QEMU. I have install QEMU and Virtual Machine Manager. Wheh I am adding smartcard reader as new device for virtual machine I get error:

> Error starting domain: unsupported configuration: this QEMU binary lacks smartcard passthrough mode support> Error starting domain: unsupported configuration: this QEMU binary lacks smartcard passthrough mode support

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 44, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 65, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1050, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 365, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: unsupported configuration: this QEMU binary lacks smartcard passthrough mode supportHost mode seems to be unsupported too. Why?Help me, please.

---

