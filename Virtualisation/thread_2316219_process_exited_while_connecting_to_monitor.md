---
title: "process exited while connecting to monitor"
date: 2016-03-06
forum: Virtualisation
---

### Post by syednoorullah92 on 2016-03-06
I am trying to create virtual machine on ubuntu using virtual machine manager i have installed kvm
but when i use display vnc for virtual machine it shows the following error  and when i use display spice it shows another error which is second one


ERROR #1

unable to complete install: 'internal error: process exited while connecting to monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg timestamp=on: Unsupported machine type
Use -machine help to list supported machines!
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1819, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 403, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 467, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg timestamp=on: Unsupported machine type
Use -machine help to list supported machines!

ERROR # 2

unable to complete install: 'unsupported configuration: spice graphics are not supported with this QEMU'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1819, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 403, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 467, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: unsupported configuration: spice graphics are not supported with this QEMU

---

### Post by MAFoElffen on 2016-03-06
You started a duplicate thread to your other thread(?):
[http://ubuntuforums.org/showthread.php?t=2316211](http://ubuntuforums.org/showthread.php?t=2316211)

---

### Post by howefield on 2016-03-06
Thread closed.

---

