---
title: "missing cpu extension during xen image boot"
date: 2012-04-04
forum: Virtualisation
---

### Post by kiminaiseah on 2012-04-04
hi , 

first of all here my computer specs and its my guinea pig-pc

i5-2400
Asus P8H67M-LE
2x 8GB DDR3 @ 1333 Kingston Value Rams
2x (Raid 0) 60GB Patriot Pyro SATA 6GB/s 
No Graphic Cards just IGP 

OS : Debian Sid/Wheezy Kernel 3.2.0-2-686-PAE

im bit confusing with my situation, 

the standard installation it  gives me the correct cpu extension with vmx & svm 

which is the requirement to run Xen-KVM,

but after installation xen-linux-system-686-pae

some of my cpu extensions are gone specially the vmx and svm and i notice also theres a new cpu extension "hypervisor"

when i restart the /etc/init.d/qemu-kvm 

the system prompting me that my computer doesnt have hypervisor

hoping for any help,

---

### Post by jao_madn on 2012-04-05
Maybe some package gives conflict to the qemu-kvm service or others..

Im not sure if my suggestion is correct. here's what happen on mine, Although its very different case. "[http://ubuntuforums.org/showthread.php?t=1920883](http://ubuntuforums.org/showthread.php?t=1920883)"

---

