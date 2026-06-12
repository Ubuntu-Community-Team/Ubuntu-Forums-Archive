---
title: "nVIDIA nForce 7xx open-source support in LinUX &gt;= 5.6"
date: 2021-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by bcschmerker on 2021-05-01
**I have a situation with an *e*machines®/ac*e*r® EL1210-09 that needs a newer VDA due to mozilla® Firefox® 87-up complaining about inadequate GFX support.**  The problem is reasonably questionable open-source support for the nVIDIA® MCP78 chipset (viz., the Ethernet, timers, DMA, PCIe bridges, Realtek audio bridge and LPC to the Super-I/O), excepting the by-passed planar C77 64-bit *geForce*® GPU.  The proposed upgrade involves replacing the MicroStar N610GT-1GD3-LP (nVIDIA® GF119) with a low-profile VDA packing a 64-bit Advanced Micro Devices® Sea Islands or Volcanic Islands GPU, which Debian supports with appropriate libraries for X.org AMDGPU; which in turn means purging the nvidia-390 support.

What has been the community experience with all-open-source kernels driving the nVIDIA nForce chipset family?  I will need to ensure a calibrated ACPI (which for me hasn't been the case before Kernel 5.4) for the system to run and stop properly.  Acer Computer, unfortunately, hasn't seen fit to release a bugfix BIOS for the DAO78L Boxer planar, and lack of documentation all but rules out a Coreboot build.  How new a Kernel family is needed for panic-free operation on all open-source, using an nForce chipset with either the intel® Pentium Processor® or the AMD® Athlon 64®?

---

### Post by mastablasta on 2021-05-03
if you want to go full opensource then avoid nvidia. the nouveau implementation lack the features fo proprietary driver and is usually good maybe only to watch some videos and desktop work. it is basically a reverse engineered driver.

---

### Post by bcschmerker on 2021-05-07
@[mastablasta](https://ubuntuforums.org/member.php?u=964486)  **As I stated, the planar C77 GPU has been by-passed; it can't drive more than one CRT or DFP with a memory limitation of 256MiB** (I need two DFP's on one GPU, which nVIDIA from Fermi and AMD from Northern Islands support)**, and the nVIDIA Tesla microarchitecture is no longer manufacturer-supported; the 340 drivers are end of life with Kernel 5.4.**  I'm referring to the balance of the nForce 780a chipset, which identify as MCP78 and MCP72 support components.

---

