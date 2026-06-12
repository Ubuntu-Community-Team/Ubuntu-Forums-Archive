---
title: "Virtual Box and installing 64bit system"
date: 2011-08-01
forum: Server Platforms
---

### Post by smoczyna on 2011-08-01
HI 

I've got a problem with installing 64bit systems on Virtual Box. It is reporting that my 64 bit virtualization abilities (something like  v-AMD or so)  are present but not enabled. There is also an advice to enable it in the bios but I can't find anything like this actually. My motherboard is Asus M4A88TD-M EVO with quad-core AMD processor.
IS there any trick to enable this feature somewhere in the system or it is a limitation of my hardware?

---

### Post by usszulu on 2011-08-01
Is your host OS 64-bit?

I am thinking that if it isn't, you can't run VirtualBox in 64-bit mode therefore you cant run the guest OS as a 64-bit?

I maybe wrong about that, or maybe you do have 64-bit installed.

Just a thought. =)

---

### Post by pqwoerituytrueiwoq on 2011-08-01
Go into your bios there is a setting involving Virtualization
My *ASUS M4A79XTD EVO* calls it* Secure Virtual Machine Mode* and it is under [I]Advanced
[/I]Does your CPU support *AMD Virtualization*?

---

### Post by smoczyna on 2011-08-10
Well,I have this option already enabled. Maybe it is processor, I don't know but if it is AMD Phenom X4 955 (or so) it should support AMD Virtualization and everything AMD-like technologies actually. 

Thanks anyway, I'll rather install 32 bit system instead.

---

### Post by Habitual on 2011-08-10
> **usszulu said:**
> Is your host OS 64-bit?

I am thinking that if it isn't, you can't run VirtualBox in 64-bit mode therefore you cant run the guest OS as a 64-bit?

I maybe wrong about that, or maybe you do have 64-bit installed.


You are not. 64bit guest OS requires a 64bit host OS.

---

