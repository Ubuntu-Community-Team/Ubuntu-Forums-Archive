---
title: "Grub Not Booting to Linux"
date: 2020-06-03
forum: Windows
---

### Post by stockdam on 2020-06-03
Hi I have Windows 10 installed on a Dell Laptop.
I installed Elementary OS as dual boot and everything was ok.
I decided to remove it by removing the partition and creating a new partition and then installed Peach OSI from USB.

Now when I boot the laptop goes to Grub Minimal BASH-Like line editing is supported.

The Boot info is here:

[http://paste.ubuntu.com/p/bRh8z3gfQz/](http://paste.ubuntu.com/p/bRh8z3gfQz/)

I tried using Boot-repair from a Live ISO of Peach and used the recommended settings. It tried to uninstall GRUB but after using the suggested commands Boot-repair still said that Grub was still present and wouldn't proceed.
It generated the following errors

W: Possible missing firmware /lib/firmware/i915/icl_dmc_ver1_07.bin for module i915
W: Possible missing firmware /lib/firmware/i915/icl_guc_32.0.3.bin for module i915
W: Possible missing firmware /lib/firmware/i915/glk_guc_32.0.3.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_32.0.3.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_32.0.3.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_32.0.3.bin for module i915
W: Possible missing firmware /lib/firmware/i915/icl_huc_ver8_4_3238.bin for module i915
W: Possible missing firmware /lib/firmware/i915/glk_huc_ver03_01_2893.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_huc_ver01_8_2893.bin for module i915

---

### Post by howefield on 2020-06-03
Moved to the "*Windows*" forum.

---

### Post by oldfred on 2020-06-03
If you directly boot from UEFI menu, the Peach entry does it boot?
You do have an old Ubuntu entry that will not work & should be removed with efibootmgr & its -b xxxx -B commands, see:
man efibootmgr
sudo efibootmgr -v
sudo efibootmgr -b XXXX -B

---

### Post by stockdam on 2020-06-03
No Peach will not boot from UEFI menu.

---

### Post by stockdam on 2020-06-04
I uninstalled Peach and installed Elementary OS and it worked perfectly. I tried Peach several times but couldn't get it to work. I assume it is an issue with Peach (never had a problem with it before on other laptops).

---

