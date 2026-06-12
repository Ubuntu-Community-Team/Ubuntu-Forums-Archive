---
title: "SR-IOV on Precise running on HP ProLiant ML310e Gen8 server"
date: 2014-06-29
forum: Virtualisation
---

### Post by Ken.Green on 2014-06-29
SR-IOV on Precise running on HP ProLiant ML310e Gen8 server


I've been trying to play with assigning devices into KVM based virtual machines and not having much joy.
One of the things I wanted to try was using SR-IOV to create virtual network functions I could assign into the VM, but I'm not even getting as far as the KVM part.

When I try to add the driver option "max_vfs=7" to igb the driver is just reporting errors "[159844.168857] igb 0000:07:00.0: **SR-IOV: bus number out of range**"


root@ml110d:~# modprobe -r igb ; modprobe igb  max_vfs=7
(I get the same result with other values than 7)

I'm running Ubuntu Precise
The server is an HP ProLiant ML310e Gen8
The NIC is an "Intel Corporation Gigabit ET Quad Port Server Adapter" based on the  82576 chipset, and reports itself as supporting SR-IOV
The card is a PCIe X4 card, although it is plugged into an X16 slot in the server.

The errors from dmesg (or the console) are


root@ml110d:~# dmesg | grep -i sr.*iov
[159844.168857] igb 0000:07:00.0: SR-IOV: bus number out of range
[159844.640910] igb 0000:07:00.1: SR-IOV: bus number out of range
[159845.115400] igb 0000:08:00.0: SR-IOV: bus number out of range
[159845.585902] igb 0000:08:00.1: SR-IOV: bus number out of range


The Ubuntu release information is


root@ml110d:~# cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
NAME="Ubuntu"
VERSION="12.04.4 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"
VERSION_ID="12.04"
root@ml110d:~#


The driver is igb and modinfo says:

root@ml110d:~# modinfo igb
filename:       /lib/modules/3.2.0-64-generic/kernel/drivers/net/ethernet/intel/igb/igb.ko
version:        3.2.10-k
license:        GPL
description:    Intel(R) Gigabit Ethernet Network Driver
author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
srcversion:     A28C671A836697D07A7BEEF
...
depends:        dca
intree:         Y
vermagic:       3.2.0-64-generic SMP mod_unload modversions
parm:           max_vfs:Maximum number of virtual functions to allocate per physical function (uint)
root@ml110d:~#


The system and BIOD information (from dmidecode)


System Information
        Manufacturer: HP
        Product Name: ProLiant ML310e Gen8
        Version: Not Specified
        Serial Number: CZ134100JC
        UUID: 30303734-3536-5A43-3133-343130304A43
        Wake-up Type: Power Switch
        SKU Number: 470065-752
        Family: ProLiant


BIOS Information
        Vendor: HP
        Version: J04
        Release Date: 11/09/2013
        Firmware Revision: 1.51

The kernel cmdline

BOOT_IMAGE=/vmlinuz-3.2.0-64-generic root=/dev/mapper/ml110d--vg-root ro console=ttyS1 intel_iommu=on intremap=no_x2apic_optout


Errors

root@ml110d:~# dmesg | grep -i sr.*iov
[159844.168857] igb 0000:07:00.0: SR-IOV: bus number out of range
[159844.640910] igb 0000:07:00.1: SR-IOV: bus number out of range
[159845.115400] igb 0000:08:00.0: SR-IOV: bus number out of range
[159845.585902] igb 0000:08:00.1: SR-IOV: bus number out of range


Hardware heirachy 

root@ml110d:~# lspci -tv
-[0000:00]-+-00.0  Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
           +-01.0-[05-08]----00.0-[06-08]--+-02.0-[07]--+-00.0  Intel Corporation 82576 Gigabit Network Connection
           |                               |            \-00.1  Intel Corporation 82576 Gigabit Network Connection
           |                               \-04.0-[08]--+-00.0  Intel Corporation 82576 Gigabit Network Connection
           |                                            \-00.1  Intel Corporation 82576 Gigabit Network Connection
           +-01.1-[09]--
           +-06.0-[02]----00.0  Hewlett-Packard Company Device 005f
           +-1a.0  Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
           +-1c.0-[0c]--
           +-1c.4-[03]--+-00.0  Broadcom Corporation NetXtreme BCM5717 Gigabit Ethernet PCIe
           |            \-00.1  Broadcom Corporation NetXtreme BCM5717 Gigabit Ethernet PCIe
           +-1c.6-[0f]--
           +-1c.7-[01]--+-00.0  Hewlett-Packard Company Integrated Lights-Out Standard Slave Instrumentation & System Support
           |            +-00.1  Matrox Electronics Systems Ltd. MGA G200EH
           |            +-00.2  Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging
           |            \-00.4  Hewlett-Packard Company Integrated Lights-Out Standard Virtual USB Controller
           +-1d.0  Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
           +-1e.0-[15]--
           +-1f.0  Intel Corporation C204 Chipset Family LPC Controller
           \-1f.2  Intel Corporation 6 Series/C200 Series Chipset Family SATA RAID Controller
root@ml110d:~#


I never find the lspci tree output too easy to map to the flat output, so tend to chase through the hierarchy using virsh nodedev-dumpxml and follow the parent upt to the top.


So chasing through from the LAN card back to the root

root@ml110d:~# virsh nodedev-dumpxml pci_0000_07_00_0
<device>
  <name>pci_0000_07_00_0</name>
  **<parent>pci_0000_06_02_0</parent>**
  <driver>
    <name>igb</name>
  </driver>
  <capability type='pci'>
    <domain>0</domain>
    <bus>7</bus>
    <slot>0</slot>
    <function>0</function>
    <product id='0x10e8'>82576 Gigabit Network Connection</product>
    <vendor id='0x8086'>Intel Corporation</vendor>
    <capability type='virt_functions'>
    </capability>
  </capability>
</device>



root@ml110d:~# virsh nodedev-dumpxml pci_0000_06_02_0
<device>
  <name>pci_0000_06_02_0</name>
  **<parent>pci_0000_05_00_0</parent>**
  <driver>
    <name>pcieport</name>
  </driver>
  <capability type='pci'>
    <domain>0</domain>
    <bus>6</bus>
    <slot>2</slot>
    <function>0</function>
    <product id='0x8018'>PES12N3A PCI Express Switch</product>
    <vendor id='0x111d'>Integrated Device Technology, Inc. [IDT]</vendor>
    <capability type='virt_functions'>
    </capability>
  </capability>
</device>



root@ml110d:~# virsh nodedev-dumpxml pci_0000_05_00_0
<device>
  <name>pci_0000_05_00_0</name>
  **<parent>pci_0000_00_01_0</parent>**
  <driver>
    <name>pcieport</name>
  </driver>
  <capability type='pci'>
    <domain>0</domain>
    <bus>5</bus>
    <slot>0</slot>
    <function>0</function>
    <product id='0x8018'>PES12N3A PCI Express Switch</product>
    <vendor id='0x111d'>Integrated Device Technology, Inc. [IDT]</vendor>
    <capability type='virt_functions'>
    </capability>
  </capability>
</device>



<device>
  <name>pci_0000_00_01_0</name>
  **<parent>computer</parent>**
  <driver>
    <name>pcieport</name>
  </driver>
  <capability type='pci'>
    <domain>0</domain>
    <bus>0</bus>
    <slot>1</slot>
    <function>0</function>
    <product id='0x0151'>Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port</product>
    <vendor id='0x8086'>Intel Corporation</vendor>
    <capability type='virt_functions'>
    </capability>
  </capability>
</device>


Now using lspci -vv to chase down through those levels of PCI bridges. This is where I get totally lost, I've no idea what most of this is telling me.

**00:00.0** Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>




**00:01.0** PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=0
        I/O behind bridge: 00004000-00005fff
        Memory behind bridge: f9f00000-fbffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [88] Subsystem: Hewlett-Packard Company Device 330b
        Capabilities: [80] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee00000  Data: 4061
        Capabilities: [a0] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 256 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #2, Speed unknown, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <8us
                        ClockPM- Surprise- LLActRep- BwNot+
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis+ BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt+ ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #0, PowerLimit 0.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
                        Changed: MRL- PresDet+ LinkState-
                RootCtl: ErrCorrectable- ErrNon-Fatal+ ErrFatal+ PMEIntEna- CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis- **ARIFwd-**
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- **ARIFwd-**
                LnkCtl2: Target Link Speed: Unknown, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [140 v1] Root Complex Link
                Desc:   PortNumber=02 ComponentID=01 EltType=Config
                Link0:  Desc:   TargetPort=00 TargetComponent=01 AssocRCRB- LinkType=MemMapped LinkValid+
                        Addr:   00000000fed19000
        Kernel driver in use: pcieport
        Kernel modules: shpchp


I notice here that "ARIFwd-" indicates that "Alternative Routing-ID Interpretation (ARI)" is disabled, it this my problem. Is this something I can change, short of buying new servers?
I've seen reference online which mention this field but nothing with any explanation.

**05:00.0** PCI bridge: Integrated Device Technology, Inc. [IDT] PES12N3A PCI Express Switch (rev 0e) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=05, secondary=06, subordinate=08, sec-latency=0
        I/O behind bridge: 00004000-00005fff
        Memory behind bridge: f9f00000-fbffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v1) Upstream Port, MSI 00
                DevCap: MaxPayload 2048 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-SlotPowerLimit 0.000W
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 256 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <512ns, L1 <4us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [c0] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UESvrt: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [200 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=4
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=02 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed+ WRR32+ WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
                        Port Arbitration Table <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp





**06:02.0** PCI bridge: Integrated Device Technology, Inc. [IDT] PES12N3A PCI Express Switch (rev 0e) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=06, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f9f00000-faefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v1) Downstream Port (Slot-), MSI 00
                DevCap: MaxPayload 2048 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag+ RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 256 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #2, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <512ns, L1 <4us
                        ClockPM- Surprise+ LLActRep+ BwNot-
                LnkCtl: ASPM Disabled; Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        Capabilities: [c0] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee00000  Data: 4079
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UESvrt: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [200 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: pcieport
        Kernel modules: shpchp





**07:00.0** Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
        Subsystem: Intel Corporation Gigabit ET Quad Port Server Adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at faee0000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at fa800000 (32-bit, non-prefetchable) [size=4M]
        Region 2: I/O ports at 4000 [size=32]
        Region 3: Memory at fa7f0000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
                Address: 0000000000000000  Data: 0000
                Masking: 00000000  Pending: 00000000
        Capabilities: [70] MSI-X: Enable+ Count=10 Masked-
                Vector table: BAR=3 offset=00000000
                PBA: BAR=3 offset=00002000
        Capabilities: [a0] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
                DevCtl: Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
                        MaxPayload 256 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #2, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <4us, L1 <64us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
                DevCtl2: Completion Timeout: 16ms to 55ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UESvrt: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Device Serial Number 00-1b-21-ff-ff-70-85-40
        Capabilities: [150 v1] Alternative Routing-ID Interpretation (ARI)
                ARICap: MFVC- ACS-, Next Function: 1
                ARICtl: MFVC- ACS-, Function Group: 0
        Capabilities: [160 v1] Single Root I/O Virtualization (SR-IOV)
                IOVCap: Migration-, Interrupt Message Number: 000
                IOVCtl: Enable- Migration- Interrupt- MSE- ARIHierarchy-
                IOVSta: Migration-
                Initial VFs: 8, Total VFs: 8, Number of VFs: 7, Function Dependency Link: 00
                VF offset: 384, stride: 2, Device ID: 10ca
                Supported Page Size: 00000553, System Page Size: 00000001
                Region 0: Memory at 00000000f9f00000 (64-bit, non-prefetchable)
                Region 3: Memory at 00000000f9f20000 (64-bit, non-prefetchable)
                VF Migration: offset: 00000000, BIR: 0
        Kernel driver in use: igb
        Kernel modules: igb




Has anyone managed to get SR-IOV working on an HP ML310e Gen8 box?
If they have, or just assigning a whole PCI card to a VM, I'd love to hear and know what configuration you have. 
Do I need to change any kernel parameters or commandline options. One option I saw online suggested setting 
pci=assign-busses but then the kernel wouldn't boot at all.

---

