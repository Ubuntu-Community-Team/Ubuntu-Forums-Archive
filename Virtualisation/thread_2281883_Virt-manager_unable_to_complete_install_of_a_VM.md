---
title: "Virt-manager unable to complete install of a VM"
date: 2015-06-10
forum: Virtualisation
---

### Post by linuxnz123 on 2015-06-10
Hi,
I am trying to boot a guest on a kubuntu 15.04. I am creating the guest using virt-manager and when i click finish i get following error message:

[HTML]
Unable to complete install: 'internal error: process exited while connecting to monitor: qemu-system-x86_64: -machine pc-i440fx-2.3,accel=kvm,usb=off: Unsupported machine type
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
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3422, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: qemu-system-x86_64: -machine pc-i440fx-2.3,accel=kvm,usb=off: Unsupported machine type
Use -machine help to list supported machines!


[/HTML]

Can you please help debug this issue? 
Thanks

---

