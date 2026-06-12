---
title: "4TB raid partition for server"
date: 2011-08-24
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-08-24
> EFI GUID Partition support works on both 32bit and 64bit platforms. You must include GPT support in kernel in order to use GPT. If you don't include GPT support in Linux kernel, after rebooting the server, the file system will no longer be mountable or the GPT table will get corrupted. By default Redhat Enterprise Linux / CentOS comes with GPT kernel support. However, *******if you are using Debian or Ubuntu Linux,******** you need to recompile the kernel. Set CONFIG_EFI_PARTITION to y to compile this feature.

Is this true?  Ubuntu has no GPT support native to the server install? 
Never compiled a kernel.  Is that of itself going to be a mind bender?  How much doo doo am I going to get into if I haven't done it a few times?  Trust me when I tell you its no thrill formatting and reformatting a 8tb raid drive or the individual disks if it screws up.  Been on that ride way too long already. Need things to go smoothly. This is not a play toy server, but will be used in a business.    

Need the advise of someone who has complied a few kernels, probably more like 10 times plus.  Where do I start and even should I, or should I try a different linux distro and not have to venture into a project where a few failures is the norm.

---

### Post by srs5694 on 2011-08-24
Whatever you're quoting is well out of date; GPT support has been included in standard Ubuntu kernels for some time now.

BTW, parted isn't the only GPT-capable partitioning tool in Linux. Anything based on libparted (parted, GParted, Palimpsest Disk Utility, or others) will do, as will the GPT fdisk tools (gdisk or sgdisk). The util-linux tools (fdisk, sfdisk, and cfdisk) can't handle GPT. The Ubuntu installer is based on libparted and so is GPT-capable.

Be aware that if you're booting from a GPT disk, you may need to include special partitions -- either a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) for BIOS-based computers or an [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) for EFI- or UEFI-based computers. If the disk isn't a boot disk, you don't need these features.

---

