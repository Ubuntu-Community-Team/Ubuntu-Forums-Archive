---
title: "KVM troubles"
date: 2008-05-07
forum: Virtualisation
---

### Post by Eil on 2008-05-07
Following the KVM docs in the Ubuntu Server Guide, I tried to get KVM working this evening and was wondering if anyone has run into this issue. I'm doing the following:

virt-install --name=ubuntu-test1 --ram=256 --file=/vps/ubuntu-test1/ubuntu-test1.img --file-size=8 --nonsparse --vnc --noautoconsole --accelerate --os-type=linux --os-variant=generic26 --hvm --cdrom=/vps/iso/Ubuntu/8.04/ubuntu-8.04-server-amd64.iso --debug

And I get the following errors:

Starting install...
libvir: QEMU error : 
libvir: QEMU error : 
libvir: QEMU error : 
Creating storage file...  100% |=========================| 8.0 GB    04:56     
libvir: QEMU error : Timed out while reading console startup output
virDomainCreateLinux() failed Timed out while reading console startup output
Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start oautoconsole'; otherwise, please
 restart your installation.
Wed, 07 May 2008 22:53:29 ERROR    virDomainCreateLinux() failed Timed out while reading console startup output
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 519, in <module>
    main()
  File "/usr/bin/virt-install", line 483, in main
    dom = guest.start_install(conscb,progresscb)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 820, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 841, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 585, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed Timed out while reading console startup output

Any ideas? I'm going to try playing around with the options tomorrow to see if any one in particular is causing it to kick.

---

