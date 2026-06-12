---
title: "VMM libvirtd/kvm pci passthrough: Unable to read from monitor"
date: 2012-07-05
forum: Server Platforms
---

### Post by ydna82 on 2012-07-05
I am having trouble getting any pci devices to pass through to guests from ubuntu 12.04 server.  I have three devices and am trying to pass them through from VMM GUI.  The VM will boot fine without any pci devices assigned to it and has bridge network connection.

As soon as I attempt to pass through a PCI device I get the following error on boot:

Error starting domain: Unable to read from monitor: Connection reset by peer

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 45, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 66, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1120, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 551, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: Unable to read from monitor: Connection reset by peer

I have been googling around and tried to look into what I may need to change on apparmor to allow pci pass through, but my problem doesn't seem to be coming from apparmor as the posts I am finding seem to state that they can actually boot up their machines when apparmor is the problem.

I have an infiniband 10Gbps network card, a Realtek wireless network card, and an ATI 7970 which I would like to be able to pass through to different VMs.  They all give me this same error message currently.

I have double checked that my bios has VT-d and all other "virtualization" options enabled that I can see, and I am fairly certain the processor is capable of pci pass through.

Anyone more familiar with qemu/kvm that could shed some light?

---

