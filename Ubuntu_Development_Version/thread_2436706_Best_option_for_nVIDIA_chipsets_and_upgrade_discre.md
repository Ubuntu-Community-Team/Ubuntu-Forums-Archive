---
title: "Best option for nVIDIA chipsets and upgrade discrete GPU's for 20.04?"
date: 2020-02-11
forum: Ubuntu Development Version
---

### Post by bcschmerker on 2020-02-11
As of 11 February 2020 I am sorting out how to keep an eMachines®/Acer® EL1210-09 upgraded with an msi® GT610 1GB DDR4 low-profile VDA (nVIDIA® GF119) and Shuttle® PC6300001 running like a top through an anticipated dist-upgrade from 18.04.3-LTS Bionic to 20.04-LTS Focal.  The EL1210-09 packs an nForce® 785 MCP chipset (with integrated 64-bit geForce® GPU C77), which I needed to by-pass for sufficient video memory; as of 11 February 2020 the EL1210 shuts down and reboots properly on the nVIDIA® CUDA&#8482; driver package for the GF119, despite support being withdrawn from the C77 itself.  (The X.org nouveau drivers always seem to run into the no-power-off issue with the nForce, where it halts after "[  OK  ] Reached target Shutdown." and doesn't actually power down or reboot.)

Do the Kernel Project and/or X Organization have a fix in progress for the no-shutdown issue with X.org Nouveau; or should I prepare to use the CUDA driver package for Focal (as i am doing for Bionic)?

---

### Post by bcschmerker on 2020-12-04
**Update:**  As of April 2020, Canonical opened the ubuntu® repository to nVIDIA Corporation for support of GPU's from Tesla to Kepler in Focal.  Same hardware, neater package collection for Kernels 5.4.0-*nn*-generic.  The 390 drivers run fine on the nF785/GF119 combo.  As of December 2020 I'm looking at GT 720 LP cards (nVIDIA GK109 GPU, 1 GiB GDDR4 VRAM) as a contingency for failure of the msi® GT610-1GD3-LP.  (I reckon that Maxwell through Ampére will need pre-boot support in the form of an **nvidia-microcode** package for GRUB 2.04 and subsequent.)

---

