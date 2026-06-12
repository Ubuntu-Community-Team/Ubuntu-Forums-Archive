---
title: "Which version of ubuntu should I load ?"
date: 2017-03-30
forum: Virtualisation
---

### Post by sammy01 on 2017-03-30
I have loaded Virtualbox on my Windows 10 PC and now am trying to load ubuntu into the virtual machine.  I tried to load 16.04.2 , then 16.10, then 14.04.5 all of them seem to load ok. Then when they go to run
they produce this error :

'This kernel requires an x86-64 CPU but only detected a i686 CPU. Unable to boot - please use a kernel appropriate for your CPU'
 
_Capture1.jpg_  below

Windows says this : 

Processor  AMD Phenom II X4 925 Processor

System type  64 bit operating system, x64 based system

_Capture2.jpg_  below

What version of Ubuntu should I use ?

Sammy01

Opps, sorry forgot the second jpg file.

---

### Post by deadflowr on 2017-03-30
*Thread moved to **Virtualisation**.*

---

### Post by sudodus on 2017-03-30
I think the problem is that the ***virtual machine*** has a 32-bit cpu. With a 64-bit cpu in the host computer and a 64-bit operating host system, it should be possible to change a setting in VirtualBox, so that the virtual machine will get a 64-bit cpu, and then your 64-bit Ubuntu will work.

---

### Post by lammert-nijhof on 2017-04-07
I think in the system tab of virtualbox you should select the PAE/NX option. You can use a 32-bits system on a 64 bits host. I have many of those from Windows 95 till Peppermint 7 and even a 16 bits OS: Windows for Workgroup 3.11. However Ubuntu itself (like most Linux systems) does not support 32 bits CPUs anymore without PAE/NX. That explains your message.

---

