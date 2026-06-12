---
title: "NPIV support for Ubuntu"
date: 2016-09-12
forum: Virtualisation
---

### Post by shepherd2 on 2016-09-12
Hi,

I am a newbie in Ubuntu. I wanted to confirm if NPIV is supported in Ubuntu 14.04?
If yes, then kindly share the process for configuring NPIV.

I have installed Ubuntu server as my base OS. With KVM i have created a guest VM on it which also runs on Ubuntu 14.04.
The base OS is connected to the storage [SAN] through a FC.
I want my Guest VM to connect to the SAN. I read that "NPIV" would help to do the trick, but i am not sure whether Ubuntu 14.04 supports and and the configuration details for NPIV.

I have checked the release notes for Xenial, it has been mentioned the NPIV is supported but only for IBM LinuxONE systems.
Not quite sure, if it is generic or exclusive for IBM.

Any help is appreciated.


Thanks in advance :smile:

---

### Post by ian-weisser on 2016-09-13
NPIV is supported in VMWare: [https://blogs.vmware.com/vsphere/2011/11/npiv-n-port-id-virtualization.html](https://blogs.vmware.com/vsphere/2011/11/npiv-n-port-id-virtualization.html)

If all you want is one VM to communicate with FC-connected hardware, NPIV seems like overkill.

The process is similar to giving the VM access to any hardware.
FC storage should be showing up as several devices (/dev/sdb, /dev/sdc, etc.).    [More info]("https://help.ubuntu.com/14.04/serverguide/multipath-devices.html")
Then edit /etc/libvirt/qemu/.xml to add the hardware.      [Example]("http://ronaldevers.nl/2012/10/14/adding-a-physical-disk-kvm-libvirt.html")

---

### Post by DuckHook on 2016-09-14
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

