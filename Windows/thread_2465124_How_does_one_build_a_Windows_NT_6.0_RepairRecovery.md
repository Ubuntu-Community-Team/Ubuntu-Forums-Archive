---
title: "How does one build a Windows NT 6.0 Repair/Recovery flash chip in LinUX?"
date: 2021-07-22
forum: Windows
---

### Post by bcschmerker on 2021-07-22
I have an *e*machines®/ac*e*r® EL1210-09 (DAO78L planar:  Advance Micro Devices Athlon LE-1620 (P/N AD1620IAS5DH); nVIDIA nForce 780a SLI with planar C77 GPU by-passed) with a buggy FADT and some other problems that the Kernel discovers consistently on startup (e.g. "AE_NOT_FOUND, While resolving a named Package Element").  The BIOS as of 22 July 2021 is Phoenix Award WorkstationBIOS R01.A0 (original to the machine); I downloaded a WorkstationBIOS R01.A3 as a ZIP and extracted it to an NTFS partition on a USB chip (as E:\Win R01A3.exe) on my ASUS® CM1630-06, only to discover that it *will not work* in Microsoft® Windows® Preinstallation Environment&#8482; 10.0.19041.1.  From a 2008 date of publication, I am estimating that I need Win 6.0.6000; my original hard drive (a 2008-vintage HGST DeskStar with Vista Home Premium preinstalled) SNAFU'd in 2010 and the EL1210 now has ubuntu® 20.04.2-LTS on a retrofit 2.5" Western Digital.  Nobody in my house runs Win 6.x any longer.  What is necessary for a Win 6.0 recovery environment on either compact-flash (I have a DURACELL® 16GB Ultra DMA available for partitioning) or USB memory chip (I have two SanDisk® Cruzers&#8482; available)?

---

### Post by CharlesA on 2021-07-22
This is a pretty stupid question, but why do you need to update the bios on this machine? Where did you download this bios update from?

---

### Post by bcschmerker on 2021-07-23
**iCentric Corporation vends upgrades for no-longer-manufacturer-supported computer systems via DriverGuide.com.**  The Page "[Gateway BIOS eMachines EL1210 Driver](https://www.driverguide.com/driver/detail.php?driverid=1730945)" has a download link for a WinZIP file BIOS_R01A3.zip, which includes a 862,732-byte self-extracting Application "Win R01A3.exe" dated 7:39:08 AM, 12 January 2009 (time zone unknown).  The BIOS-provided map has e820 from mem 0x0000000000000000 to 0x000000013fffffff in nine segments.  The Kernel detected several BIOS bugs (from /var/log/dmesg.*n*):
```
...
[    0.019921] kernel: ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid length but zero Address: 0x0000000000000000/0x1 (20200528/tbfadt-615)
...
[    0.095514] kernel: AGP: Node 0: aperture [bus addr 0x1c000000-0x1dffffff (32MB)
[    0.095516] kernel: Aperture pointing to e820 RAM. Ignoring.
[    0.095517] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.095519] kernel: AGP: Please enable the IOMMU option in the BIOS Setup
[    0.095520] kernel: AGP: This costs you 64MB of RAM
[    0.095524] kernel: AGP: Mapping aperture over RAM [mem 0xb4000000-0xb7ffffff] (65536KB)
...
[    0.230898] kernel: ACPI Error: AE_NOT_FOUND, While resolving a named reference package element - \_PR_CPU0 (20200528/dspkginit-438)
...
```
The stock Phoenix Award WorkstationBIOS hasn't a specific option for IOMMU (Enabled/Disabled).  I have Virtualization enabled in the Setup utility.

---

### Post by CharlesA on 2021-07-23
Are you sure the system board and CPU support IOMMU? The CPU was released in 2007 and I can't find any info that says it supports it.

If you are dead set on updating the bios to a version released in 2008 (R01A3.BIN), you'll have to install Windows and run the Winflash utility.

I would recommend installing a copy of Windows Vista since you said this machine came with Vista if you go that route.

---

### Post by bcschmerker on 2021-07-24
**Advance Micro Devices Incorporated used an early I/O memory map called the K8 Graphics Address Remapping Table (GART) in the Athlon 64 series main processing units (Socket AM2).**  GART was part of the Accelerated Graphics Port Interface specification.  The Kernel has since evolved to support more sophisticated IOMMU's than are integrated into the AMD Athlon 64 Series (including the stock LE-1620 in the EL1210-09); it has several relevant command-line options for boot, including but not limited to: ```
gart_fix_e820={ on | off }
``` for Athlon 64 systems in addition to: ```
amd_iommu={ fullflush | off | force_isolation }
amd_iommu_intr={ vapic | legacy }
iommu={ off | force | noforce | biomerge | panic | nopanic | merge | nomerge | forcesac | soft | pt | nobypass | noagp }
```

---

