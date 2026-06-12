---
title: "poor IO performance KVM"
date: 2011-10-08
forum: Server Platforms
---

### Post by yyagol on 2011-10-08
Hi All , 

I am not so sure this is ubuntu problem but , when i try testing
guest FReeBSD under KVM , i get a very poor IO performance ,
write speed of 7M/s instead of 245M/s that my disk can handle .
i have tried using raw device with LVM but that didnt change anything.
any help would do 

spec : 
KVM :         QEMU emulator version 0.14.1
system :      ubuntu 11.10
Kernel :      Linux PC 3.0.0-12-generic x86_64
Mem:          8GB
CPU:          Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
HD:           1TB WDC WD1002FAEX-0



update : found out that FreeBSD did not support virtio , test it with VirtualBox and works fine

---

