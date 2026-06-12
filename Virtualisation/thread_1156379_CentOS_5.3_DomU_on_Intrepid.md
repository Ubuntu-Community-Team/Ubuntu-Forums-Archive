---
title: "CentOS 5.3 DomU on Intrepid"
date: 2009-05-11
forum: Virtualisation
---

### Post by warpig on 2009-05-11
Hi All,

Apologies if this question has already been raised.  I'm trying to install a CentOS 5.3 guest in Xen on Ubuntu 9.04.  I'm using the virt-manager wizard to do this.  The contents of the CentOS DVD is available via NFS.  The local disk image is created successfully and then I get the following error:

Unable to complete install '<class 'libvirt.libvirtError'> unknown OS type xen
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 718, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 926, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 966, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 973, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: unknown OS type xen
'

I don't believe I'm missing any libraries on my local machine, but I could be wrong.  If you need any more information, I'm happy to provide it.

Thanks,
Leigh

---

### Post by Shamballajones on 2010-02-04
I also got this error on a vanilla install of Centos 5.4. 

In that case the solution appeared to be to delete the default qemu localhost in the Virtual Machine Manager and replace it with a domain0 that uses xen as the hypervisor. After that I was able to create domUs without seeing the error.

---

