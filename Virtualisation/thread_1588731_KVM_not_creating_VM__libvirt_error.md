---
title: "KVM not creating VM :: libvirt error"
date: 2010-10-05
forum: Virtualisation
---

### Post by piine on 2010-10-05
I am currently running Ubuntu Server 10.04 AMD64 with kvm, qemu-kvm, virt-install, vmbuilder and every time I try to create a amd64 VM, I receive this error 
```

root@beast:/media/tb15/ISOs/Ubuntu# sudo virt-install -n lucid_amd64 -r 512 -f /media/tb2/VMz/lucid_amd64.img  -s 20 -c qemu:///system --accelerate --connect=qemu:///system  --vnc --noautoconsole --cdrom /media/tb15/ISOs/Ubuntu/ubuntu-10.04.1-server-amd64.iso  -v --os-type=linux


Starting install...
Creating storage file luc   0% |                         |   20 B 10108868:15 ETCreating storage file luc 100% |=========================|  20 GB    00:00     
ERROR    internal error cannot parse QEMU version number in ''
Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start lucid_amd64'; otherwise, please
 restart your installation.
ERROR    internal error cannot parse QEMU version number in ''
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 943, in <module>
    main()
  File "/usr/bin/virt-install", line 839, in main
    start_time, guest.start_install)
  File "/usr/bin/virt-install", line 894, in do_install
    dom = install_func(conscb, progresscb, wait=(not wait))
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 660, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 758, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1097, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error cannot parse QEMU version number in ''

```I have searched all over the internet the last 48 hours (need to get this running in a hurry) and have found very little info. Can someone please help!!!!!!!!!!!!!!!!

---

### Post by piine on 2010-10-05
I think I may have found a fix, maybe. I decided to enabled the pre-release update in apt-sources and it seems to be cooperating at the moment. However, if anyone knows anything about this particular error, please comment. Thanks a bunch.

---

