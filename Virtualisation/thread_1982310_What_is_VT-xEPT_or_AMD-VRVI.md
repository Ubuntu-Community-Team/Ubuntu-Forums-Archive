---
title: "What is VT-x/EPT or AMD-V/RVI  ?"
date: 2012-05-18
forum: Virtualisation
---

### Post by Docmero on 2012-05-18
[CENTER]What is what is VT-x/EPT or AMD-V/RVI ?
I'm using Ubuntu 11.10 (host) and Win 7 64 bit (gust , Vmware) 
I have Core i5 750
I noticed this option is unchecked in the Virtual machine settings 
What is it's importance ?
Thanks
[/CENTER]

---

### Post by lukeiamyourfather on 2012-05-18
Those features allow for hardware acceleration of virtualization for near native performance of virtual machines. Its also required for 64-bit guests. If your hardware supports this definitely enable it. If it doesn't work and your hardware supports it check the BIOS of the host to make sure its enabled, some machines come with this disabled in the BIOS by default.

---

### Post by Docmero on 2012-05-18
> **lukeiamyourfather said:**
> Those features allow for hardware acceleration of virtualization for near native performance of virtual machines. Its also required for 64-bit guests. If your hardware supports this definitely enable it. If it doesn't work and your hardware supports it check the BIOS of the host to make sure its enabled, some machines come with this disabled in the BIOS by default.

The host and the guest are both 64 bit .
My mobo is Asus P7P55D E Pro . I don't know if it supports this feature or not !!

---

### Post by lukeiamyourfather on 2012-05-18
> **Docmero said:**
> The host and the guest are both 64 bit .
My mobo is Asus P7P55D E Pro . I don't know if it supports this feature or not !!

The support for it is based on the processor. Chances are it does. Pretty much anything made in the last five years will support it.

---

