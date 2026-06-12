---
title: "Lucid 10.04 beta KVM virtual image on Ubuntu 9.10"
date: 2010-03-22
forum: Virtualisation
---

### Post by codfather on 2010-03-22
Hi,
I have spent this morning trying to successfully build a Qemu/KVM virtual image of the latest Lucid 10.04 beta release without success. The installation works perfectly until the VM re-boots after a successful install from the ISO and then it complains about a disk defect and never continues. The ISO image used to build this has been used to build VM's with Virtualbox 3.1.4 without an issue so the installation media is of know good quality.

Hardware used:
Dell 6400 Inspiron Lappy
CPU Intel Core 2 Duo P8700 2.53Ghz
4GB RAM
Intel i915 Compatible Graphics Adapter

Host operating system:
Ubuntu 9.10
Kernel 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux
libvirt 0.7.0-1ubuntu13.1
qemu-kvm 0.11.0-0ubuntu6.3

Virt-machine setup:
512 MB RAM
1 vCPU
5 GB vdisk storage using the virtio driver
Bridged networking
Display left as VNC on 127.0.0.1


If any more information is required then I can post. I have searched the forums and Googled , but can only find a bug on using the virtio disk driver, which doesn't appear to be affecting this scenario.

---

### Post by codfather on 2010-03-22
After further research it indeed does appear down to the virtio storage drive. If you swap out that driver for a SCSI qemu driver 10.04 now not only install's but runs perfectly after a reboot.

Unfortunately the SCSI driver is no where near as fast as the virtio driver, so I will report this as a bug.

Nick

---

### Post by codfather on 2010-03-22
This has been reported as Bug #544345 on launchpad

---

