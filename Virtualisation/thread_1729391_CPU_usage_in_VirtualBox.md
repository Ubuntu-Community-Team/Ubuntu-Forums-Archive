---
title: "CPU usage in VirtualBox"
date: 2011-04-14
forum: Virtualisation
---

### Post by Diametric on 2011-04-14
Oi,

Does anyone know how a dual core 64 bit processor is used in a VM?  Meaning, I have a dual core 64 bit intel processor - when I create a VM ( I usually give a full core to the guest OS) does it default to 32 bit or when I give the guest OS it's own core, is that 64 bit?  I ask so that I am maximizing both host and guest OS on my VM's.  I hope this makes sense.

Thanks!

---

### Post by d3v1150m471c on 2011-04-14
if you're running a 32bit guest on a 64 bit processor then it's 32 bit. Otherwise 64bit is 64bit is 64bit :)

---

### Post by squenson on 2011-04-14
The 32- or 64-bit is defined at the moment of the installation of the OS. If you installed a 64-bit OS, it uses 64-bit instructions and a fraction of the total processor power of your machine.

---

### Post by Diametric on 2011-04-14
I think I gotcha - if I give a full core to the guest os and install it as a 64 bit OS, then it will run as a 64 bit with out issue?  Thanks for your quick reply.

Cheers.

---

