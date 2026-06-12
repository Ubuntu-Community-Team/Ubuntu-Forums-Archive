---
title: "USB device (webcam) in XP under KVM"
date: 2008-06-29
forum: Virtualisation
---

### Post by ss08 on 2008-06-29
Is it possible to get XP installed with KVM-QEMU to see connected USB devices? There is an option -usbdevice which seems like it will do something of the sort.
I'm specifically trying to get my webcam detected. It works in Ubuntu (Camorama). 
My lsusb looks like this:
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 026: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  

When I give the option -usbdevice 003:046d:08f0 with kvm, I get the error:
Warning: could not add USB device 003:046d:08f0

Any pointers?

---

### Post by tors on 2008-07-19
FYI

[http://qemu-forum.ipi.fi/viewtopic.php?t=4424&p=13474](http://qemu-forum.ipi.fi/viewtopic.php?t=4424&p=13474)

[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/+viewstatus)

---

