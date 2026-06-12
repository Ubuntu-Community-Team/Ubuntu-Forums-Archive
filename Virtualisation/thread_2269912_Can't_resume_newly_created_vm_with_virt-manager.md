---
title: "Can't resume newly created vm with virt-manager"
date: 2015-03-18
forum: Virtualisation
---

### Post by Marcos_Bianchi on 2015-03-18
Hi,
after creating a virtual machine using virt-manager, it starts and immediately changes its state to "Paused". When I try to unpause, the following error appears:

Error unpausing domain: internal error: unable to execute QEMU command 'cont': Resetting the Virtual Machine is required

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 117, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1181, in resume
    self._backend.resume()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1784, in resume
    if ret == -1: raise libvirtError ('virDomainResume() failed', dom=self)
libvirtError: internal error: unable to execute QEMU command 'cont': Resetting the Virtual Machine is required


In libvirt.log appears: 2015-03-19 01:33:01.116+0000: 1231: error : qemuMonitorJSONCheckError:354 : internal error: unable to execute QEMU command 'cont': Resetting the Virtual Machine is required

Running Ubuntu 14.04.1 inside VMware Player 6.
AMD svm support checked.

Any ideas?

Thanks!

---

### Post by TheFu on 2015-03-19
Whoa .... you're trying to run a hypervisor inside a hypervisor?  Not a good idea for non-experts.

---

