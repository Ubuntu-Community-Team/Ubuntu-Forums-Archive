---
title: "ubuntu 18-04 server LTS"
date: 2019-12-27
forum: Server Platforms
---

### Post by cosy2 on 2019-12-27
```
[drm:intel_bios_init [i915]] *ERROR* Unexpected child device config size 39 (expected 38 for VBT version 228)
```

i got this strange error on boot and i dont really understand what is the problem 

how i get the error

1 enabled secure boot in the bios


disabling secure boot to legacy it removes this error

---

### Post by CelticWarrior on 2019-12-27
Disabling Secure Boot should be fine, Legacy likely not.

IF UEFI then always install in UEFI mode. Enabling/disabling Secure Boot is optional an not related to Legacy. Meaning: You don't need to change to Legacy to disable Secure Boot.

---

