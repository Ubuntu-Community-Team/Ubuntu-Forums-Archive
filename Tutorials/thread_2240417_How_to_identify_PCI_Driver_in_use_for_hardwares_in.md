---
title: "How to identify PCI Driver in use for hardwares in Ubuntu of similar distro?"
date: 2014-08-19
forum: Tutorials
---

### Post by rousseau09 on 2014-08-19
This guide shows how you can identify PCI Driver Chipset Information on Linux. Often users troll different forums and blogs to find out they can identify which driver their PCI or USB device is using. This guide applies to all possible scenarios. After reading and following this guide you will be able to identify the followings:

**Link to complete post:**

[How to identify PCI Driver in use for hardwares in Ubuntu of similar distro?]("http://www.blackmoreops.com/2014/08/20/identify-pci-usb-wired-wireless-driver-linux-identify-pci-driver/")

```
Contents

    Examples of PCI devices
    What is Peripheral Component Interconnect or PCI?
    Question: How do I identify PCI driver for anything in Linux?
        Identify PCI Driver Chipset Information in Linux
            Step 1: List all PCI devices – Identify PCI driver
            Step 2: Get verbose output for selected device – Identify PCI driver
            Step 3: Get driver info for selected device – Identify PCI driver
            Step 4: NVIDIA – Identify PCI driver dilemma
            Step 5: More ways to Identify PCI driver details
                Step 5.1: Identify PCI driver using lspci -k command
                Step 5.2: Identify PCI driver using lshw command
                Step 5.3: Identify PCI driver using lshw-gtk tool
    Summary
```


 
```
Examples of PCI devices

    Identify PCI driver for Processor – CPU
    Identify PCI driver for Motherboards
    Identify PCI driver for Communication controllers
    Identify PCI driver for Network devices
    Identify PCI driver for USB devices
    Identify PCI driver for USB controllers
    Identify PCI driver for High Definition Audio Controller
    Identify PCI driver for VGA or graphics cards
    Identify PCI driver for Memory (RAM)
    Identify PCI driver for Thermal Control Registers
    Identify PCI driver for Ethernet devices
    Identify PCI driver for DVD R/W devices
    Identify PCI driver for Blueray devices
    Identify PCI driver for CDROM devices
```

In short, any device drivers can be identified that is using plugged into a PCI slot.

```
This guide will work for any Linux distributions, namely -

    Linux Mint
    Ubuntu
    Debian GNU/Linux
    Mageia / Mandriva
    Fedora
    openSUSE / SUSE Linux Enterprise
    Arch Linux
    CentOS / Red Hat Enterprise Linux
    PCLinuxOS
    Slackware Linux
    Puppy Linux
    Kali Linux (my distro ;) )
```

**Link to complete post:**

[How to identify PCI Driver in use for hardwares in Ubuntu of similar distro?]("http://www.blackmoreops.com/2014/08/20/identify-pci-usb-wired-wireless-driver-linux-identify-pci-driver/")

Step 1: List all PCI devices – Identify PCI driver

```
root@kali:~# lspci
```

This will give you a sample output like the following:
```

root@kali:~# lspci
(some output removed)
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
root@kali:~#
```

Now you can see the device names, types and some funky numbers at the front. (highlighted in bold-red).

 
Step 2: Get verbose output for selected device – Identify PCI driver

Let’s say we want to identify the driver used my Linux kernel for Ethernet controller (which is the wired port on my motherboard).

00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)

Copy the number’s at the front i.e. 00:19.0 and use it with lspci command to find more info

```
root@kali:~# lspci -vv -s 00:19.0
```

This will give you an output like below:

```
root@kali:~# lspci -vv -s 00:19.0
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 8000
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 46
    Region 0: Memory at faec0000 (32-bit, non-prefetchable) [size=128K]
    Region 1: Memory at faefa000 (32-bit, non-prefetchable) [size=4K]
    Region 2: I/O ports at d000 [size=32]
    Capabilities: [c8] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0f00c  Data: 4192
    Capabilities: [e0] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: e1000e
```

So the Kernel is using a driver named e1000e.

 
Step 3: Get driver info for selected device – Identify PCI driver

Now to get the full details of the driver you issue the following command:

```
root@kali:~# modinfo e1000e
```

This will list everything and anything for that driver including the driver file.

```
root@kali:~# modinfo e1000e 
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.3.2-k
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     875CF610ED4160DBA055BB2
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        ptp
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
```

So the driver file used for this particular Network Controller is:

 

```
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
```

So now you know the device name, details, driver used, vendor, publisher, dependencies, license and Author details for the selected PCI device.

There's two parts to this post, PCI and USB Driver. I am sure many users bump into the problem on how to identify a particular driver file used by a hardware and this post will help you to exactly pinpoint the driver name, filename and complete details. 

**Link to complete post:**

[How to identify PCI Driver in use for hardwares in Ubuntu of similar distro?]("http://www.blackmoreops.com/2014/08/20/identify-pci-usb-wired-wireless-driver-linux-identify-pci-driver/")



I hope it is of use to you.

---

