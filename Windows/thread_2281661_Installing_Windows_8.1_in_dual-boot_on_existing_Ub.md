---
title: "Installing Windows 8.1 in dual-boot on existing Ubuntu system"
date: 2015-06-08
forum: Windows
---

### Post by whit-launchpad on 2015-06-08
Google is not being my friend as I look for recipes for installing Windows 8.1 on an existing Ubuntu (15.04) system. There's a disk partition already reserved for Windows, and I've set up dual-boot systems with grub in years past. But I'm seeing no advice that doesn't assume a system has Windows on it first - and there's no desire to blow away the existing Ubuntu here. Is it as simple as pointing the Windows installer to the right partition, and then re-installing grub once it's done? Or are there tricks and gotchas involved?

Thanks.

---

### Post by yancek on 2015-06-08
> Is it as simple as pointing the Windows installer to the right partition, and then re-installing grub once it's done?

It used to be about that simple but with windows 8, you need to deal with UEFI and Secure Boot.  One major factor is that if you have Ubuntu installed UEFI then windows 8 must also be UEFI, conversely if Ubuntu is MBR then windows must also be MBR.  I don't use UEFI so won't advise but there are a lot of posts here about UEFI with Ubuntu/windows.  Someone should be along shortly with advice.

---

### Post by whit-launchpad on 2015-06-09
> **yancek said:**
> It used to be about that simple but with windows 8, you need to deal with UEFI and Secure Boot.  One major factor is that if you have Ubuntu installed UEFI then windows 8 must also be UEFI, conversely if Ubuntu is MBR then windows must also be MBR.  I don't use UEFI so won't advise but there are a lot of posts here about UEFI with Ubuntu/windows.  Someone should be along shortly with advice.
Thanks. That leaves open the question of what it takes to convert an Ubuntu MBR installation to UEFI, assuming this is going to be required. **Update:** Looks like it can be: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).

---

### Post by whit-launchpad on 2015-06-13
Keeping notes here as I go along, so at least there will be some record of doing things in the Linux first, then Windows order. 

It looks like I don't have to convert to UEFI: "**Windows 8/8.1** **x86_64** versions support booting in x86_64  UEFI mode from GPT disk only, OR in BIOS mode from MBR/msdos disk only.  They do not support IA32  UEFI boot, x86_64 UEFI boot from MBR/msdos  disk, or BIOS boot from GPT disk." - [https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot](https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot). (While I slightly prefer the Ubuntu/Debian universe to Arch, Arch often has the best documentation - although in this case it does not answer the question about installing Windows to an existing Linux system, either with UEFI or MBR.)

---

