---
title: "KVM error in Hardy"
date: 2008-05-14
forum: Virtualisation
---

### Post by itsme_n8 on 2008-05-14
Hi all, thanks for reading.  I'm running Hardy on my laptop, and in an effort to break my dependency from my Windows partition, I'm trying to install Win XP Pro into a KVM.  I had Gusty (64 bit), and upgraded to Hardy.  I'm using the GUI because I'm not strong with CLI (although I would like to learn).Please let me know what other information would be useful and I will supply it.  

Here is the error message I get.  This is AFTER I have: set the Name of the VM, the location for the Installation files (a CD), RAM, CPU, then the Virtual Hard Drive.  All that is successful, it's once I finally try  to install I get this:

```

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed Cannot find QEMU binary /usr/bin/qemu-system-x86_64: No such file or directory

Traceback (most recent call last):

  File "/usr/share/virt-manager/virtManager/create.py", line 620, in do_install

    dom = guest.start_install(False, meter = meter)

  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 820, in start_install

    return self._do_install(consolecb, meter)

  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 841, in _do_install

    self.domain = self.conn.createLinux(install_xml, 0)

  File "/usr/lib/python2.5/site-packages/libvirt.py", line 585, in createLinux

    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)

libvirtError: virDomainCreateLinux() failed Cannot find QEMU binary /usr/bin/qemu-system-x86_64: No such file or directory

'

```

Please help.

Nate

---

### Post by ericy on 2008-05-14
> libvirtError: virDomainCreateLinux() failed Cannot find QEMU binary /usr/bin/qemu-system-x86_64: No such file or directory

Looks like you didn't install qemu.
(If you have "hardware acceleration" checked, it's possible that you haven't added your id to kvm's group list).

---

### Post by itsme_n8 on 2008-05-14
ericy, thanks for the response.

I think I am confused.  I thought the Virtual Machine Manager was a gui for QEMU, and XEN, and I was under the impression that KVM was just a flavor of QEMU.  Do I need to install QEMU specifically?  I really don't want to do that, I'd like to use KVM, are there any other GUI's for KVM?

I don't know if I have hardware acceleration checked.  How would I check that, and if it is, how would I add my id's to kvm's group list?

Hhmmm.... it sucks when going through this raises more questions.  :)

Nate

---

### Post by sndnichols on 2008-05-14
KVM and Qemu work together. KVM works "on" the hardware, while qemu is more of an emulator. When combined, you get hte best of both worlds. At least that is my understanding. Maybe this will help some [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

