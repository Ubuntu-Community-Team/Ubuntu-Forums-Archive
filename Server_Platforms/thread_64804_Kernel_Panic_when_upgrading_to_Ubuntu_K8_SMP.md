---
title: "Kernel Panic when upgrading to Ubuntu K8 SMP"
date: 2005-09-12
forum: Server Platforms
---

### Post by xLnT on 2005-09-12
Hello..
I have installed Ubuntu 5.04 and the install works perfect.
I can do everything i am supposed to do.. apt-get, login, ssh works.

But when i installed linux-amd64-k8-smp i get Kernel Panic Error (the same when i tried Debian).
The kernel Panic looks as follows:
[img]http://www.excellent-servers.se/error.jpg[/img]

And i have the following hardware:

1x Tyan K8SE
2x Opteron 270 (Dualcore cpus)
4x 512Mb Kingston DDR400 ECC/Reg

I have testet my hardware and there's nothing wrong with it.

//Magnus

---

### Post by LordHunter317 on 2005-09-12
Have you patched the motherboard to support 2x dualcore CPUs?  If you take a single CPU out, does everything start working?

---

### Post by xLnT on 2005-09-12
I dont know what you mean with patched the motherboard.. but i have flashed the motherboard whith the latest bios, if thats what you mean?
I have not tried to remove on cpu..
Someone told me that it could be memoryproblem..and gave me a tips to only use one memorymodule.

//Magnus

---

### Post by LordHunter317 on 2005-09-12
Well, unless the BIOS update said it added support for 2x dual-core CPU, there's more than a fair chance it simply won't work.

---

### Post by sandyw on 2005-09-21
I have a dual 242 opteron on Tyan Tiger S2875 MBD.
Pleaase can you tell me the /etc/apt/sources.list changes for the Linux-amd64-k8-smp metapackage 
Can find the linux-k7-smp which is running sweetly, but no can get the k8-smp
Thanks in advance
Sandyw  ](*,)

---

