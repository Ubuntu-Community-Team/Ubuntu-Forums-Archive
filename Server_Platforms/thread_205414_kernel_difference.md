---
title: "kernel difference"
date: 2006-06-28
forum: Server Platforms
---

### Post by ashrack on 2006-06-28
What is the diff betwenn normal ubuntu kernel
```
Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
```
and server one:
```
Linux kernel image for version 2.6.15 on Server Equipment
```
Which would be better for the following UBUNTU roles:
DHCP,DNS SERVER
FIRESTARTER FIREWALL+internet sharing for 5client PC
running eMule or torrent almost 24/7

---

### Post by knn on 2006-06-28
[QUOTE=ashrack]What is the diff betwenn normal ubuntu kernel
```
Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
```
and server one:
```
Linux kernel image for version 2.6.15 on Server Equipment
```
Which would be better for the following UBUNTU roles:
DHCP,DNS SERVER
FIRESTARTER FIREWALL+internet sharing for 5client PC
running eMule or torrent almost 24/7[/QUOTE]

The desktop kernel (normal) is optimized for low latency desktop use. Applications can preempt the kernel (i.e. take over processing power), giving you lower total processing power, but increased responsiveness. This is especially important for a multimedia desktop.
Server kernels are configured in a different way. The kernel cannot be preempted, so the system may feel less responsive sometimes, but you'll have more raw processing power. I'd try the server kernel

---

### Post by ashrack on 2006-06-28
how come that SERVER kernel doesnt have any special optimizations for K7 or 686 like the normal kernels do?

---

### Post by ashrack on 2006-06-29
[QUOTE=ashrack]how come that SERVER kernel doesnt have any special optimizations for K7 or 686 like the normal kernels do?[/QUOTE]
anyone

---

### Post by knn on 2006-06-29
[QUOTE=ashrack]anyone[/QUOTE]

Well, maybe the Ubuntu maintainers didn't want to compile a separate kernel for 686 and k7, so they only included generic optimizations.

---

