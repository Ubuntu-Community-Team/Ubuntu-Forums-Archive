---
title: "Chrome"
date: 2020-06-27
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-06-27
Had problems with Chrome. Got a system hang when using Google Maps.
Was fixed by turning off "Use hardware acceleration when available" in Chrome settings, but that's not an ideal solution. Found another solution after some googling
Enter the following line in /etc/default/grub
 [B]GRUB_CMDLINE_LINUX="amdgpu.gpu_recovery=1 amdgpu.lockup_timeout=3000"

[/B]Worked only a couple of times. Strange that going to a page in Chrome hangs the computer and forces a hard restart with the power button or reset button.
No problem in Fedora 32 and Windows 10. 
Chromium works fine on Ubuntu, but  you need Widevine to use e.g. Netflix and I have not managed to install Widevine in the snap version of Chromium.

Changed kernel to Kernel: 5.7.6-050706-generic x86_64 and this fixed the problem with Chrome

---

