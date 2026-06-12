---
title: "IOMMU Groups on Skylake - Xeon E3-1275v5 / Supermicro X11SAE-F"
date: 2016-10-15
forum: Virtualisation
---

### Post by francoislepage on 2016-10-15
Hello,

I'm trying to setup the following system based on the above mentionned configuration.

_Ubuntu 16.10 host_
- Samsung SSD 850 PRO RAID 1 (2x)
- Intel HD Graphics P530

_FreeNAS Guest_
- LSI/Avago 9300-8i HBA Adapter *passthrough*
[U]
Windows 10 Guest[/U]
- AMD Radeon HD 6850 *passthrough*

I first realized that Ubuntu 16.04 does not suport properly ACS capability on Skylake.  More on this [here]("https://ubuntuforums.org/showthread.php?t=2329053"). (refer to IOMMU Groups bellow).  A fix have been introduced in Kernel 4.7 which is now incorporated in 4.8, hence availaible in Ubuntu 16.10.

Putting this aside for now, the problem I have is that it seems that the LSI/Avago HBA  Adapter is clustered with the AMD Radeon card under IOMMU Group #1 (inserted into CPU SLOT #6 and #4), when with adequate IOMMU support for Skylake.
[COLOR=#000080]
**I would like to know if there is anything to do at this point to passthrough the AMD Radeon and the LSI/Avago Adapters to differents guests?  Or wiill both PCI-E x16 and x8 will always have to be passed to the same guest?**[/COLOR]

Thanks for your help!!!




_Here is the IOMMU Groups before and after the upgrade :_

**IOMMU Groups under Ubuntu 16.04 LTS**
```
IOMMU group 0
    00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:1918] (rev 07)
IOMMU group 1
    00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07)
    00:01.1 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x8) [8086:1905] (rev 07)
    01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Barts PRO [Radeon HD 6850] [1002:6739]
    01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
    02:00.0 Serial Attached SCSI controller [0107]: LSI Logic / Symbios Logic SAS3008 PCI-Express Fusion-MPT SAS-3 [1000:0097] (rev 02)
IOMMU group 2
    00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:191d] (rev 06)
IOMMU group 3
    00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
IOMMU group 4
    00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    00:16.3 Serial controller [0700]: Intel Corporation Sunrise Point-H KT Redirection [8086:a13d] (rev 31)
IOMMU group 5
    00:17.0 RAID bus controller [0104]: Intel Corporation C600/X79 series chipset SATA RAID Controller [8086:2826] (rev 31)
IOMMU group 6
    00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #1 [8086:a110] (rev f1)
    00:1c.2 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #3 [8086:a112] (rev f1)
    00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #5 [8086:a114] (rev f1)
    00:1c.6 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #7 [8086:a116] (rev f1)
    00:1c.7 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #8 [8086:a117] (rev f1)
    03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242]
    04:00.0 PCI bridge [0604]: Tundra Semiconductor Corp. Device [10e3:8113] (rev 01)
    05:00.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
    06:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
    07:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7164 [1131:7164] (rev 81)
    08:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7164 [1131:7164] (rev 81)
IOMMU group 7
    00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1)
IOMMU group 8
    00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a149] (rev 31)
    00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
    00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
IOMMU group 9
    00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)[/HTML]

```

**IOMMU Groups under Ubuntu 16.10**
```

IOMMU group 17
    07:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7164 [1131:7164] (rev 81)
IOMMU group 7
    00:1c.2 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #3 [8086:a112] (rev f1)
IOMMU group 15
    04:00.0 PCI bridge [0604]: Tundra Semiconductor Corp. Device [10e3:8113] (rev 01)
    05:00.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
IOMMU group 5
    00:17.0 RAID bus controller [0104]: Intel Corporation C600/X79 series chipset SATA RAID Controller [8086:2826] (rev 31)
IOMMU group 13
    00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)
IOMMU group 3
    00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
IOMMU group 11
    00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1)
[COLOR=#000080]IOMMU group 1
    00:01.0 PCI bridge [0604]: Intel Corporation Skylake PCIe Controller (x16) [8086:1901] (rev 07)
    00:01.1 PCI bridge [0604]: Intel Corporation Skylake PCIe Controller (x8) [8086:1905] (rev 07)
    01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Barts PRO [Radeon HD 6850] [1002:6739]
    01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
    02:00.0 Serial Attached SCSI controller [0107]: LSI Logic / Symbios Logic SAS3008 PCI-Express Fusion-MPT SAS-3 [1000:0097] (rev 02)[/COLOR]
IOMMU group 18
    08:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7164 [1131:7164] (rev 81)
IOMMU group 8
    00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #5 [8086:a114] (rev f1)
IOMMU group 16
    06:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
IOMMU group 6
    00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #1 [8086:a110] (rev f1)
IOMMU group 14
    03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242]
IOMMU group 4
    00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    00:16.3 Serial controller [0700]: Intel Corporation Sunrise Point-H KT Redirection [8086:a13d] (rev 31)
IOMMU group 12
    00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a149] (rev 31)
    00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
    00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
IOMMU group 2
    00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics P530 [8086:191d] (rev 06)
IOMMU group 10
    00:1c.7 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #8 [8086:a117] (rev f1)
IOMMU group 0
    00:00.0 Host bridge [0600]: Intel Corporation Skylake Host Bridge/DRAM Registers [8086:1918] (rev 07)
IOMMU group 9
    00:1c.6 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #7 [8086:a116] (rev f1)

```

---

### Post by T.J. on 2016-10-17
I usually do not work with Intel hardware (too overpriced), but I believe there is an ACS moderator patch so that you can pass-though items from groups without the rest.  I can't tell you more than that, or if it is even still used.  You may have to do a little research in that regard.


I do have a few questions, please do not think I am being rude - I'm just sort of blunt.


1. If the Radeon is a discrete card, have you tried a different slot?  By moving it to a different slot, you can place it in a different IO group, depending on your motherboard.
2.  If there a compelling reason to upgrade to 16.10 (which is intended as a developer version), as it has only 6 months of patches and support? You could just switch kernels, patch the existing kernel or compile your own.  16.10 is going to be very buggy, especially for early adopters.  Running virtualization in 16.04 (or any other LTS) is a much safer and more reliable thing to do.  I'm not criticising you by asking. I'm trying to understand your needs and abilities.

---

