---
title: "Unsupported machine type Use -machine help to list supported machines"
date: 2016-03-06
forum: Virtualisation
---

### Post by syednoorullah92 on 2016-03-06
[COLOR=#FF0000]
[COLOR=#2F4F4F]
I am trying to create virtual machine on ubuntu 15.10 using virtual machine manager i have installed kvm
but when i use display vnc for virtual machine it shows the following  error  and when i use display spice it shows another error which is  second one[/COLOR]


ERROR #1

> unable to complete install: 'internal error: process exited while  connecting to monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg  timestamp=on: Unsupported machine type
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
libvirtError: internal error: process exited while connecting to  monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg timestamp=on:  Unsupported machine type
Use -machine help to list supported machines!

ERROR # 2

> unable to complete install: 'unsupported configuration: spice graphics are not supported with this QEMU'

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
[/COLOR]

---

### Post by MAFoElffen on 2016-03-06
Are you doing via *which* py script? What is the host OS and what is the guest you where installing?

Did you run the script with elevated permissions? (sudo)

---

### Post by syednoorullah92 on 2016-03-06
i am using virtual machine manager and ubuntu 15.10 as host OS and i trying to install win7 and ubuntu as guest but same error for both

---

### Post by MAFoElffen on 2016-03-07
If continuing to try to use kvm-spice with virt-manager, then the video cpu type should be set to qxl... With Spice emulation , it's a server/client relationship. that needs to be installed in both (appropriate pieces guest and host)

---

