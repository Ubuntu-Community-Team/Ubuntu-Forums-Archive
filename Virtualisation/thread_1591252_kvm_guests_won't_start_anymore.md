---
title: "kvm guests won't start anymore"
date: 2010-10-09
forum: Virtualisation
---

### Post by slooow on 2010-10-09
Hi,

I am running lucid on a x86 desktop. I had a windows XP guest and ubuntu lucid server guest. Both were running (except windows had no sound, but that is another problem..) But now I cannot start them anymore. 

Here is the message I am getting:

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error cannot parse QEMU version number in ''


It does not matter if I start it as a normal user or root. I tried on virt-manager as well as virsh. I found a bug report regarding apparmor interfering with kvm but that doesn't apply to me. I am a bit out of my depth getting my head around how kvm, libvirt and qemu work together. What else can I do to investigate the problem?
:confused:
Ivo

---

### Post by jmaccini on 2011-06-08
I know this is a year late, but I was just searching for this exact problem and could not find a solution... However, I was able to resolve my issue by simply uninstalling qemu and reinstalling it using:
```
sudo apt-get remove qemu-kvm
sudo apt-get install qemu-kvm
```

---

