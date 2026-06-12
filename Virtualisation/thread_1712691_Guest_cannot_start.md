---
title: "Guest cannot start"
date: 2011-03-23
forum: Virtualisation
---

### Post by dmaina on 2011-03-23
I have a KVM guest that has failed.
 

It was working before, i shut it down to take a latest snapshot, but when i run it, it fails with below errors:
 

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: operation failed: failed to retrieve chardev info in qemu with 'info chardev'
 

I have other guests on the same VM Host and all are working.
 

System Info:
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid
 

$qemu-kvm       0.12.3+noroms-0ubuntu9.4



$kvm            1:84+dfsg-0ubuntu16+0.12
 

$uname -a
Linux MyVMHost 2.6.32-29-server #58-Ubuntu SMP x86_64 GNU/Linux
 

$free -m
             total       used       free     shared    buffers     cached
Mem:          8000       7294        706          0         47       2808
-/+ buffers/cache:       4437       3563
Swap:        11603          8      11595
 

$df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vmhost2-root
                      447G  318G  121G  73% /
none                  4.0G  252K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G  160K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sda1             228M   51M  166M  24% /boot


Been searching the internet but nothing works.

 

Any one with a solution/work-around i will greatly appreciate.

---

