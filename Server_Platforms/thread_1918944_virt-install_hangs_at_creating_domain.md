---
title: "virt-install hangs at creating domain"
date: 2012-02-02
forum: Server Platforms
---

### Post by GusBricker on 2012-02-02
Hi,
I'm new to Ubuntu Server, but not to linux. Im running Ubuntu Server 11.10 x64 on a VIA Epia P820 motherboard, the CPU is VIA 64 bit CPU.

I've tried installing two guests. Windows 2k8 and Ubuntu 11.10 (non server edition).

For the Windows 2k8 install, i used the following command:

sudo virt-install --connect qemu:///system --name win2k8 --ram 512 --graphics vnc,password=something,listen=127.0.0.1 --os-type=windows --os-variant win2k8 --disk path=/var/lib/libvirt/images/win2k8,size=100,format=vmdk -c /home/chris/win2k8_x64.iso --hvm

This causes the installer to hang at "Creating Domain" step indefinitely. At this point, the SSH connection hangs up as well. Basically the entire server stops responding. The only way to recover it is to hit the reset button... I get the same result when i try do the Ubuntu install.

I've run:
egrep -c '(vmx|svm)' /proc/cpuinfo
Which returns 1. Saying my processor supports virtualisation.

I've also run:
kvm-ok 
Which returns:
INFO: /dev/kvm exists
KVM acceleration can be used

Basically I've followed all the instructions on the Ubuntu server documentation. Some help would be greatly appreciated!

Thanks

---

