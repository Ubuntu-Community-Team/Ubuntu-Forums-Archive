---
title: "libvirt.libvirtError: internal error: libxenlight state driver is not active"
date: 2020-07-27
forum: Virtualisation
---

### Post by marietto2008 on 2020-07-27
On Ubuntu 20.04 while running the Xen kernel (I have been able to boot succesfully a phisical installation of windows 10 in dom U with the passed through graphic card (rtx 2080 ti),so the xen kernel is working right),I get the error "libxenlight state driver" is not active when I try to create a new connection to my XEN domain (localhost) using virt-manager:

Unable to connect to libvirt xen:///.

internal error: libxenlight state driver is not active

Verify that:
 - A Xen host kernel was booted
 - The Xen service has been started

Libvirt URI is: xen:///

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 956, in _do_open
    self._backend.open(connectauth.creds_dialog, self)
  File "/usr/share/virt-manager/virtinst/connection.py", line 172, in open
    conn = libvirt.openAuth(self._open_uri,
  File "/usr/lib/python3/dist-packages/libvirt.py", line 104, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')

libvirt.libvirtError: internal error: libxenlight state driver is not active

Package versions that might be relevent:

virt-manager: (1:2.2.1-3ubuntu2).

xen_version : 4.14-unstable

libvirt-bin:

  Installed: 1.2.2-0ubuntu13.1

virsh --version = 6.0.0

libvirtd --version
libvirtd (libvirt) 6.0.0

---

