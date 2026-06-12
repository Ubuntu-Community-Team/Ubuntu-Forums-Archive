---
title: "Installer Crash - Win11Pro Hyper-V - 32GB vDisk"
date: 2023-12-10
forum: Virtualisation
---

### Post by naxal on 2023-12-10
Hello,

Following are the hardware details,

AMD Ryzen 5 1600 (no oc, full stock)
MSI A320 Chipset board
16GB (8x2) 2666 DDR4
Nvidia 730 2GB GPU
WD SN570 NVMe (Windows Boot & Software)
Crucial SATA SSD (Ubuntu Hyper-V vDisk)
WD 1TB SATA HDD (ubuntu server iso)
Windows 11 Pro (Latest, up-to-date, on default release channel, no beta or such)

I am using the latest Ubuntu Server ISO (latest 22.04.3 ISO) for the installation. Problem is, strangely the installer crashes every time when I try to install on 32GB vdisk with default partition scheme along with lvm set to max size available on default partition scheme. Installation works fine with anything lower or higher on vDisk value.

The crash happens as soon as I hit done on that partition page to proceed further

Bug or something wrong with my system?

Thanks.

---

### Post by MAFoElffen on 2023-12-10
Hyper-V services from Win10 or Win11?

Hyper-V Guest as gen1 or Gen2?

How much ram allocated for the guest? How many vcpu's?

Let me reboot into Windows and see... I haven't had any troubles prior to this... BRB

---

### Post by MAFoElffen on 2023-12-10
Posted from Win10-- Hyper-V Gen 2 VM, 4GB RAM, 32GB VM Disk. SecureBoot Disabled. Installed fine.

Sorry. I could not recreate that problem.

---

### Post by naxal on 2023-12-10
Hello,

> **MAFoElffen said:**
> Hyper-V services from Win10 or Win11?

Hyper-V Guest as gen1 or Gen2?

How much ram allocated for the guest? How many vcpu's?

Let me reboot into Windows and see... I haven't had any troubles prior to this... BRB

Windows 11 Pro Hyper-V
Guest is Gen 2
Secure Boot Turned off
TPM is turned off
RAM for Guest OS didn't matter, I tried 2 / 4 GB option
All 12 vCPU allocated.

Thanks.

---

