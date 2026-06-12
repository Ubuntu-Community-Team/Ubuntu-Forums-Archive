---
title: "Error with libvirt when trying to create a virtual machine with KVM on Ubuntu 9.10"
date: 2010-03-31
forum: Virtualisation
---

### Post by codfather on 2010-03-31
I haven't found anything relating to this error in this forum or on Google as of yet.

Kernel version on host:2.6.31-20-generic-pae #58-Ubuntu
Laptop: Dell 6400 
Intel P8700 CPU with VT extensions enabled in BIOS
KVM kernel modules loaded and checked:
kvm_intel              43848  0 
kvm                   162560  1 kvm_intel
4GB RAM

When I run the following command:
**sudo virt-install --connect qemu:///system --name test6 --ram 1000 --disk path=/home/nick/vmmachines/kvm.img,size=5 --network network:default  --accelerate --vnc --cdrom /home/nick/isos/ubuntu-10.04-beta1-desktop-i386.iso --os-type=linux**

I get the following error:

[B]Starting install...
Creating storage file...  100% |=========================| 5.0 GB    00:00     
internal error unable to start guest: libvir: error : cannot execute binary /usr/bin/qemu-kvm: Permission denied

Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start test6'; otherwise, please
 restart your installation.
ERROR    internal error unable to start guest: libvir: error : cannot execute binary /usr/bin/qemu-kvm: Permission denied
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 780, in <module>
    main()
  File "/usr/bin/virt-install", line 678, in main
    start_time, guest.start_install)
  File "/usr/bin/virt-install", line 733, in do_install
    dom = install_func(conscb, progresscb, wait=(not wait))
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 541, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 633, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1077, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error unable to start guest: libvir: error : cannot execute binary /usr/bin/qemu-kvm: Permission denied
[/B]

I also get a similar error if using virt-manager, so I thought I would double check from the command line to make sure. The exact same error occurs.

Any light someone can shed on this will be gratefully received.

As an aside, I have one VM working, created as a normal user, and not as root using virt-manager, but it didn't create an xml file in /etc/libvirt/qemu. Does anyone know where these are supposed to be stored if not here?

Thanks in advance.

Nick

---

### Post by codfather on 2010-05-04
Exactly the same problems with Ubuntu 10.04, latest version of virt-manger etc.

Can anyone shed any light on what might be causing this problem?

Nick

---

### Post by TheR on 2010-05-09
I would't know what to do about your error. I sometimes get strange errors about access permissions when some file or path doesn't exist.

I don't know where does KVM saves it settings. I didn't bother since you I can always get current settings with:

virsh dumpxml myvirtmachine > dump.xml

update dump.xml and then:

virsh define dump.xml


by
TheR

---

