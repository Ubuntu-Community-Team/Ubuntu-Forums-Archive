---
title: "Error during kernel update"
date: 2016-09-19
forum: Ubuntu Development Version
---

### Post by cdysthe on 2016-09-19
Hi,

I got the 4.8 kernel in an upgrade today on the 16.10 Beta 1. During install a DKMS module was build for my Broadcom wlan card. At the end I got the following error:

Generating /boot/initrd.img-4.8.0-11-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915

I seem to remember that i915 has to do with Intel graphics. I am afraid if I boot the new kernel my display won't work. Anyone know what this error really means?

---

### Post by cariboo on 2016-09-20
I just got the kernel update, I got the same error messages during the update. I rebooted, and so far haven't run into any problems.

---

### Post by cdysthe on 2016-09-20
> **cariboo said:**
> I just got the kernel update, I got the same error messages during the update. I rebooted, and so far haven't run into any problems.


I found a solution. Tha missing  firmware can be downloaded from Intel and installed using their installer. Take a look at this thread, first response: 

[http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs](http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs)

The error disappeared for me after that.

---

### Post by Doug S on 2016-09-20
> **cdysthe said:**
> I found a solution. The missing  firmware can be downloaded from Intel and installed using their installer. Take a look at this thread, first response: 

[http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs](http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs)

The error disappeared for me after that.Yes, that was my answer. You only need the stuff if you actually have the processor in question. I've been ignoring the errors for months.

---

