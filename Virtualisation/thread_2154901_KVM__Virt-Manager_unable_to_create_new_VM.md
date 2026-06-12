---
title: "KVM / Virt-Manager unable to create new VM"
date: 2013-06-16
forum: Virtualisation
---

### Post by RagnarokXIX on 2013-06-16
I hope someone can help me my boss asked me to setup KVM on his laptop that is running Ubuntu 12.10 64bit with encrypted LVM.
I am getting the below message when trying to create the first Virtual Machine.  Unfortunately our linux engineer is on vacation an I'm 
a Windows engineer with only basic linux skills, so please keep your suggestions simple so that a noob like me can follow them.

Unable to complete install: 'internal error Process exited while reading console log output: char device redirected to /dev/pts/1
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
libvirtError: internal error Process exited while reading console log output: char device redirected to /dev/pts/1
Could not access KVM kernel module: Permission denied
failed to initialize KVM: Permission denied
No accelerator found!

---

