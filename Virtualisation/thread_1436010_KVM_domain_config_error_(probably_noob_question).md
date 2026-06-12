---
title: "KVM domain config error (probably noob question)"
date: 2010-03-22
forum: Virtualisation
---

### Post by parazitus on 2010-03-22
Hi!

I'm trying to set up kvm on my ubuntu 9.04 AMD64 installation. I'm sort of a noob so my question might be very simple to solve, or at least I hope so.

I followed the following tutorial to install and set up a VM in kvm:
[http://howtoforge.org/virtualization-with-kvm-on-ubuntu-9.04-p2](http://howtoforge.org/virtualization-with-kvm-on-ubuntu-9.04-p2)

This failed for me when I tried to build the VM using "vmbuilder kvm ubuntu ...".
I got the following error from libvirt:

```

2010-03-22 11:21:21,115 INFO     Converting /tmp/vmbuilderodXDwP/disk1.img to qcow2, format /var/vms/my-vm1/disk1.qcow2
libvir: Domain Config error : unknown OS type hvm
2010-03-22 11:21:51,785 INFO     Cleaning up
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/vm.py", line 463, in create
    self.deploy()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/vm.py", line 182, in deploy
    if getattr(plugin, 'deploy')():
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/libvirt/__init__.py", line 65, in deploy
    self.conn.defineXML(vmxml)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1012, in defineXML
    if ret is None:raise libvirtError('virDomainDefineXML() failed', conn=self)
libvirt.libvirtError: unknown OS type hvm

```Any ideas on what the problem is and how to fix it?


Thanks!

para

---

