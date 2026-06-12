---
title: "Nvidia or Nouveau : big power usage increase"
date: 2018-04-24
forum: Ubuntu Development Version
---

### Post by fthx on 2018-04-24
Since today or yesterday, I get a high power usage running my Optimus laptop.
Nouveau or Nvidia, same issue : 5 W -> 15 W. Seems to not power off the dGPU.

There was absolutely no issue at the end of last week, since I measured power usage with Powertop and it was fully ok.

I don't know what's gone wrong, i didn't change any setting but I got some kernel and Nvidia updates last days.

---

### Post by fthx on 2018-04-24
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1765363](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1765363)

---

### Post by mc4man on 2018-04-24
Using nvidia on an optimus here, don't see that file, (/proc/acpi/bbswitch),  nor is any bbswitch package installed or needed.

---

### Post by fthx on 2018-04-25
I don't understand your bbswitch reference ? That's not the point here ?

Well, the issue lands using Nvidia proprietary when Prime is running Intel. The Nouveau module is loaded and the dGPU is not powered off.
Additionally, if I uninstall the Nvidia driver (-> Nouveau) when prime-intel is set, the config is not fully deleted (grub option nouveau pm), causing dGPU to not be powered off using Nouveau.

---

### Post by mc4man on 2018-04-25
> **fthx said:**
> I don't understand your bbswitch reference ? That's not the point here ?

Well, the issue lands using Nvidia proprietary when Prime is running Intel. The Nouveau module is loaded and the dGPU is not powered off.
Additionally, if I uninstall the Nvidia driver (-> Nouveau) when prime-intel is set, the config is not fully deleted (grub option nouveau pm), causing dGPU to not be powered off using Nouveau.
Well the bug you linked (at 1st. thought you filed, not the case) , is an older 18.04 install using older conf's, methods  & some useless packages installed. That user, Tim, had several issues only on that install, some resolved by updating his conf's, that bug possibly by doing a fresh install with current 18.04 image on that machine. Or maybe not..

Anyway it was him who still has bbswitch installed & mentions prominently in bug description.
A more useful bug should be filed using the latest 18.04 image as starting point..

As far as laptop (optimus) machines, I've 3 different ones here, none have any issue switching from Intel to Nvidia or Nvidia to Intel  drivers. Nouveau is never used.

---

### Post by fthx on 2018-04-26
Well, I'm currently running nvidia-390 with prime set to intel.
```
~$ lsmod | grep nouveau
nouveau              1716224  2
ttm                   106496  1 nouveau
mxm_wmi                16384  1 nouveau
wmi                    24576  7 dell_wmi,wmi_bmof,intel_wmi_thunderbolt,dell_wmi_descriptor,mxm_wmi,nouveau,dell_smbios_wmi
i2c_algo_bit           16384  2 nouveau,i915
drm_kms_helper        167936  2 nouveau,i915
drm                   401408  20 nouveau,i915,ttm,drm_kms_helper
video                  40960  4 dell_wmi,dell_laptop,nouveau,i915
```

I managed to solve the issue (for my config anyway) :
- remove nouveau from PM excluded devices from TLP
- remove the nouveau.runpm=0 option from grub (created by prime when switching to intel)
- reboot, obviously
Some users in french forum noticed that some nvidia GPU hang with nouveau, so I can just tell it works for my quadro M1000M.

The issue (in my case) is not about switching between nvidia and intel, it's about nvidia gpu power management when switching to intel mode.

---

