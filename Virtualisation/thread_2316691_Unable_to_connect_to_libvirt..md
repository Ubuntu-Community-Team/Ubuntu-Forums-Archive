---
title: "Unable to connect to libvirt."
date: 2016-03-10
forum: Virtualisation
---

### Post by syednoorullah92 on 2016-03-10
I installed xen 4.5 from Repository and virt-manager and it was  working fine but when i removed xen 4.5 and compiled and installed xen  4.6  the virtual machine manager is unable to connect to xen it shows  the following error...

  ```
 Unable to connect to libvirt.

internal error: libxenlight state driver is not active

Verify that:
 - A Xen host kernel was booted
 - The Xen service has been started

Libvirt URI is: xen:///

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 1050, in _open_thread
    self._backend.open(self._do_creds_password)
  File "/usr/share/virt-manager/virtinst/connection.py", line 158, in open
    open_flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: internal error: libxenlight state driver is not active
```

---

### Post by MAFoElffen on 2016-03-10
ssh into your Xen server's IP. (if you cannot connect, go to it physically and confirm system and networking settings...)
```

sudo dmidecode -s system-product-name
sudo dmesg | grep -i Xen
sudo cat /sys/hypervisor/uuid

```
The first command would query the system for a product code. If it is running a hypervisor, it will show the hypervisor as the machine code, instead of the physical machine's id code.

The second command will look foe Xen in the system log and tell you if it is running or had any problems.

If using Xen and running, the thrid commonad will look at the hypervisor UUID. You are looking for all zeros, which would indicate that it is running as Dom0. If not all zero's, then running as DomU. If not there, then not running Xen.

---

