---
title: "KVM Kernel Module - Permission Denied"
date: 2013-05-31
forum: Virtualisation
---

### Post by WilliamStuttgart on 2013-05-31
Hey Community,

I'm trying to run a Windows7 Image on my Ubuntu 12.04 in Virtual Machine Manager. But I don't know what to do with this error message - maybe you can help me:
Actually I thought I installed everything properly, since I added my user to the kvm group.


> Unable to complete install: 'internal error Process exited while reading console log output: char device redirected to /dev/pts/0
Could not access KVM kernel module: Permission denied
failed to initialize KVM: Permission denied
No accelerator found!
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 45, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1909, in do_install
    guest.start_install(False, meter=meter)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1236, in start_install
    noboot)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1304, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 2166, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error Process exited while reading console log output: char device redirected to /dev/pts/0
Could not access KVM kernel module: Permission denied
failed to initialize KVM: Permission denied
No accelerator found!



---

