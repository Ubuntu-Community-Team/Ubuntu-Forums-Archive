---
title: "KVM Virtio Network Drivers with Windows Server 2003 R2 on Ubuntu 13.10"
date: 2014-02-21
forum: Server Platforms
---

### Post by xrctp1 on 2014-02-21
I have a Windows Server 2003 R2 (x64) virtual machine running on an Ubuntu 13.10 KVM host that will not allow me to install the redhat-provided drivers. Every time I try to install the virtio driver for the network I get the error "The parameter is incorrect."

I have tried re-downloading the driver iso, and modifying the .inf file (changing the 1001 to 1000 and back per suggestions). Nothing has yielded any positive results.

Chkinf reports "InfFile->getSection() called with invalid section name: RedHat." every time.

---

### Post by xrctp1 on 2014-02-24
Finally got it working. For anyone else that runs into this issue here's what I did:

Shut down the VM.
Added secondary adapter and configured it for virtio.
Booted and installed virtio driver for secondary adapter.
Shut down and then swapped the adapter types in the VM configuration.
Booted and installed driver to primary interface.

---

