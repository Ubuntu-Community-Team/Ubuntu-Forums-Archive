---
title: "Any idea of why virt-install barfs about 'xen' not supported, on a kvm system?"
date: 2010-09-24
forum: Virtualisation
---

### Post by Henry P on 2010-09-24
Hi

Any idea of what causes
```
ERROR    Host does not support virtualization type 'xen'
```Any hints on what has gone wrong?

Isn't virt-install suppose to work with both xen and kvm?

Ubuntu:
```

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```Linux tuts 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

```
virt-install -n alpha --accelerate --vnc  --paravirt --ram 1024 --file-size=26 --file=/var/images/alpha.kvm --cdrom=/home/goid/Downloads/install-x86-minimal-20100921.iso --os-type=linux --os-variant=gentoo  --virt-type=kvm
```I've installed kvm following the instructions on: [https://wiki.ubuntu.com/kvm](https://wiki.ubuntu.com/kvm)

```
 virsh version
Compiled against library: libvir 0.7.5
Using library: libvir 0.7.5
Using API: QEMU 0.7.5
Running hypervisor: QEMU 0.12.3

```lsmod | grep kvm
kvm_amd                36420  0 
kvm                   285496  1 kvm_amd


  Thanks

    Henry

---

