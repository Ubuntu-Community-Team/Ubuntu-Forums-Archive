---
title: "kvm windows xp  shut down start up severe trouble"
date: 2009-11-02
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-02
getting some severe shutdown startup problems with xp and kvm
it always restarts with error and i have to try the last known good configuration

when i shut it down it says it is still running in virt manager and i get a warning window
i have to keep retrying the last known good and maybe after 3 or 4 times it comes up with a good boot

> Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 507, in shutdown_domain
    vm.shutdown()
  File "/usr/share/virt-manager/virtManager/domain.py", line 551, in shutdown
    self._update_status()
  File "/usr/share/virt-manager/virtManager/domain.py", line 202, in _update_status
    info = self.vm.info()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 530, in info
    if ret is None: raise libvirtError ('virDomainGetInfo() failed', dom=self)
libvirtError: operation failed: could not query memory balloon allocation


---

### Post by sdowney717 on 2009-11-02
[http://www.linux-kvm.com/content/unable-gracefully-shutdown-guest-windows-2003-server](http://www.linux-kvm.com/content/unable-gracefully-shutdown-guest-windows-2003-server)

looks like a known bug.

---

