---
title: "MBR doesn't show Windows 10"
date: 2019-08-26
forum: Ubuntu/Debian BASED
---

### Post by dyeghikoo on 2019-08-26
Hi,

I know is a common question but I have tried ALL and I really don't get it.

I have installed Windows in SDA disk & then I installed POP!_ (Ubuntu 18) in SDB. 

I have 2 problems:

- The first one is the GRUB doesn't starts automatically so I have to push shift when I turn on my laptop.
- The second one is the GRUB doesn't show Windows 10 so I can't access to Windows 10. 

I have my BIOS in Legacy Mode & Secure Boot disabled.

[http://paste.ubuntu.com/p/q2NrCcy9N9/](http://paste.ubuntu.com/p/q2NrCcy9N9/)

---

### Post by oldfred on 2019-08-26
Moved to Other OS since not Ubuntu, but maybe should be Windows sub-forum.

How did you install Windows & did it boot after install?

Your Windows install on sda, has gpt partitioning. Windows only boots in UEFI mode from gpt partitioned drives, but you have no UEFI Windows boot in your UEFI entries. 
It almost looks like your Windows boot files were on sdb, and main install on sda. So when you installed Pop, it overwrote the Windows boot files. Windows uses default boot drive setting in UEFI/BIOS as location to install its boot partitions.

Windows & Ubuntu install in boot mode UEFI or BIOS, that you boot install media. Since UEFI system probably better to always boot in UEFI mode. But some like the now 35 year old BIOS/MBR configuration.

Grub will not install to sda's MBR for BIOS boot as with gpt partitioning you need a tiny 1 or 2MB unformatted partition with the bios_grub flag. But normally on gpt partitioned drives you have an ESP - efi system partition for UEFI boot.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by dyeghikoo on 2019-08-27
You were right. Pop overwrote the Windows boot files.

Thank you so much!!!

---

