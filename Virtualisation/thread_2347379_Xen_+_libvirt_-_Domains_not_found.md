---
title: "Xen + libvirt - Domains not found"
date: 2016-12-24
forum: Virtualisation
---

### Post by evag0ras7 on 2016-12-24
I have installed a VM with Xen Hypervisor (xl commands) , but when I try to view the information about the VM through the libvirt (lookupByName/lookupByID), I have the following error:

libvirt: Xen Light Driver error : Domain not found
Traceback (most recent call last):
  File "lookupByID.py", line 11, in <module>
    dom = conn.lookupByID(domainID)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3867, in lookupByID
    if ret is None:raise libvirtError('virDomainLookupByID() failed', conn=self)
libvirt.libvirtError: Domain not found

---

