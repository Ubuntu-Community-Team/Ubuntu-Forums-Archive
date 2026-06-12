---
title: "KVM virt-manager cannot create a VM"
date: 2010-09-11
forum: Virtualisation
---

### Post by DBQ on 2010-09-11
Hi everybody. When I try to create a VM in ubuntu (Lucid) using virt-manager, I get the following error. Can anyone help me please? The name of my VM is "test".

```

Unable to complete install '<class 'libvirt.libvirtError'> internal error Unable to find cgroup for test

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 1436, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 660, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 758, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1097, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error Unable to find cgroup for test

'

```

---

### Post by drumbug1 on 2010-09-14
Looks very similar to this reported bug at RedHat - looks like it's not actually a bug.  

[https://partner-bugzilla.redhat.com/show_bug.cgi?id=607790](https://partner-bugzilla.redhat.com/show_bug.cgi?id=607790)

Daniel Berrange says:
> 
This error normally occurs because someone has modified the system cgroups
configuration after libvirtd had started. Can you restart libvirtd and see if
the problem goes away.

---

