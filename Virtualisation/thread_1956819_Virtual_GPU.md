---
title: "Virtual GPU"
date: 2012-04-11
forum: Virtualisation
---

### Post by medic2000 on 2012-04-11
Hi,

I want to virtualize Windows inside of my Linux installation. My objective is playing games. Is virtualing the GPU impossible?

My rig:

ASUS P8Z68-V PRO GEN-3
Intel Sandy Bridge i5-2500k
8 GB RAM
GeForce GTX 560 Ti
120 GB OCZ Vertex SSD
1 TB Western Digital Caviar Black

---

### Post by dcstar on 2012-04-12
> **medic2000 said:**
> Hi,

I want to virtualize Windows inside of my Linux installation. My objective is playing games. Is virtualing the GPU impossible?



No. VMs provide their own virtualised video environment.

---

### Post by medic2000 on 2012-04-12
> **dcstar said:**
> No. VMs provide their own virtualised video environment.

XEN provides direct VGA passthrough.

---

### Post by CharlesA on 2012-04-12
> **medic2000 said:**
> XEN provides direct VGA passthrough.
True, but that is more of a specialized solution. It would be easier just to dual boot and run the games from Windows instead of trying it inside a VM as VMs aren't made for gaming.

---

