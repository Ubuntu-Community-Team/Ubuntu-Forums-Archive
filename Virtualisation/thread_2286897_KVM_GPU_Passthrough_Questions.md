---
title: "KVM GPU Passthrough Questions"
date: 2015-07-15
forum: Virtualisation
---

### Post by ipeek90 on 2015-07-15
My main question is does the 14.04 kernel work with GPU pass through without any kernel patches? 

**1) Hardware:**
```

Mobo - MSI 970A-G43
CPU - AMD FX-6300
GPU - AMD HD7870(Guest OS/Windows) - First PCIe Slot
GPU - AMD R7 240(Host OS/Linux) - Second PCIe Slot
```

MoBo has IOMMU enabled
I  can not switch those 2 around as far as where on the Mobo they're  being used as I have a water cooler on my 7870 and it does not fit on  the second PCIe slot.

**2) What is being passed through?**
I want the R7 to be used for Xubuntu.
The 7870 to be passed through to Win7, as well as a keyboard for initial setup(will use something else afterwards)

**3) Seabios was what I used on 14.04**

When using the 14.04(unpatched) version I was able to pci_stub my 7870 card but QEMU would throw errors when trying to use the device.

```
qemu-system-x86_64: vfio_bar_write(,0xd2ea, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2e9, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2e8, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2ef, 0x0, 1) failed: Device or resource busy

```

[COLOR=#00000A][FONT=sans-serif]I did a fresh install of  15.04 as my attempted at an upgrade rendered my machine unusable. I am still having issues.
[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]Now when I stub out the 7870 and reboot I get nothing from the r7 card. I can TTY and see items from the 7870 but no GUI.[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]I went ahead and tried out the 4.0.2 & 4.0.4 kernels as well...
[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]When I stub out the 7870 the thing boots and the 7870 just displays a flashing "_". The R7 displays "activate" but are completely black and will not show anything.[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]
Here is the output from lscpi -nn[/FONT][/COLOR]
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition] [1002:6818]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240] [1002:6613]
02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
```
[COLOR=#00000A][FONT=sans-serif]
And /etc/initramfs-tools/modules[/FONT][/COLOR]
```
pci_stub ids=1002:6818,1002:aab0
```
[COLOR=#00000A][FONT=sans-serif]
Some additional information I realized...[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]The 3.19 kernel see's the R7 in "additional drivers" and also sees an "unknown device" The 4.0.x kernels see the 7870 in "additional drivers" and sees the same "unknown device"[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]I'm at a loss here. The upgrades seem to have made the issue worse. And now my DE is all busted looking.
[/FONT][/COLOR]
[COLOR=#00000A][FONT=sans-serif]I know both cards are being used right this moment because my right screen is DVI to the R7 and my Left screen is DVI to the 7870 and VGA to the R7. Both screens are using DVI...SO I know they're both being utilized. I just cant figure out why the R7 is not displaying anything when I stub out the 7870.

I've also tried using the pci_stub.id in the /etc/default/grub:

[/FONT][/COLOR]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on vfio_iommu_type1 pci_stub.ids=1002:6818,1002:aab0"
```

However this still did not work. The 7870 gets stubbed out but the r7 never gets initialized. Rather than before when the screens would turn on but not display anything, now the screens simply do not get any signal from the r7.
I can run dmesg | grep stub and it shows the 7870 beinging stubbed out but thats as it.
I also tried without the audio ID in the stub line.

---

### Post by KillerKelvUK on 2015-07-15
Hi, 14.04 does support passthrough...kernel patching only becomes necessary if you experience certain issues that come about because of vendor hardware designs or the combination of hardware and software specific to your use case needs it.

I'm a little confused by your setup though so if you could start with clarifying this first...

1) what is your host hardware (mobo, gfx for host only+additional)
2) what hardware do you want to passthrough to the guest?
3) are you using legacy Seabios in the guest or OVMF?

As the audio hardware on both the cards is the same your pci_stub arguments would affect both cards but just only the audio portion on the 2nd card...I'd recommend you simplify this for the moment by making your stub only for the video adapter of the card you wish to pass through...i think from your post this is the 7870 which means your stub just needs to be for 1002:6818.

Once you've done this and rebooted the host run the following and post back the results...

```

sudo lspci -d 1002: -vvv

```

Do you know if you have iommu group separation of your devices?  If not I've attached a shell script which will output your devices by group, run this on your host and post back the results...

```

sh /path/to/iommu.sh

```

---

### Post by ipeek90 on 2015-07-15
Glad to hear that 14.04 does support it.

Here is some extra details I should have included in the OP.

**1) Hardware:**
```

Mobo - MSI 970A-G43
CPU - AMD FX-6300
GPU - AMD HD7870(Guest OS/Windows) - First PCIe Slot
GPU - AMD R7 240(Host OS/Linux) - Second PCIe Slot
```

MoBo has IOMMU enabled
I can not switch those 2 around as far as where on jthe Mobo they're being used as I have a water cooler on my 7870 and it does not fit on the second PCIe slot.

**2) What is being passed through?**
I want the R7 to be used for Xubuntu.
The 7870 to be passed through to Win7, as well as a keyboard for initial setup(will use something else afterwards)

**3) Seabios was what I used on 14.04**

I won't be in front of this machine again until tomorrow. I will post the outcome of those commands tomorrow evening after I reinstall 14.04

Thanks for the help.

---

### Post by KillerKelvUK on 2015-07-15
Just some further observations then till you're back with the box...

14.04 does support passthrough but the stock version of qemu isn't the latest, think its v2.0.  I don't think this makes a big difference for AMD passthrough but it would if you were using an Nvidia card, reason being is that from qemu v2.1.1 there is a feature to hide the fact that KVM is running from the virtual machine...this is needed to get the Nvidia drivers to work inside the guest.

If you're using legacy Seabios you're likely hitting a VGA arbitration issue [http://vfio.blogspot.co.uk/2014/08/whats-deal-with-vga-arbitration.html](http://vfio.blogspot.co.uk/2014/08/whats-deal-with-vga-arbitration.html), this is where kernel patching comes in if you can't switch to using OVMF instead.  If you can switch to use OVMF you need to use the latest pure image from from [https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/) (just grab the x64 rpm and open it with an archive manager, find the folder with the OVMFs and extract the OVMF-pure-EFI.fd).  The reason you might not be able to switch to OVMF is because you also need to check that your 7870 has an EFI vBIOS as per [http://vfio.blogspot.co.uk/2014/08/does-my-graphics-card-rom-support-efi.html](http://vfio.blogspot.co.uk/2014/08/does-my-graphics-card-rom-support-efi.html) (I noted the first comment at the end of the link about your card 7870...depending on your card vendor this could be a problem for you!).

Step at a time though, grab the other stuff as you note and post back.

EDIT:  Just read this... [http://vfio.blogspot.co.uk/2015/04/progress-on-amd-front.html](http://vfio.blogspot.co.uk/2015/04/progress-on-amd-front.html)

---

### Post by ipeek90 on 2015-07-15
I don't believe my manufacture does the proper vBIOS for the 7870. It's a Sapphire card. A quick Google search says its a no go.

---

### Post by KillerKelvUK on 2015-07-15
> **ipeek90 said:**
> I don't believe my manufacture does the proper vBIOS for the 7870. It's a Sapphire card. A quick Google search says its a no go.

Okay, well as you're not using IGP this maybe okay so stick with the Seabios for now and see where you get to.

---

### Post by ipeek90 on 2015-07-15
So am  I still looking at a potential VGA patch or is that for the Intel IGP?

---

### Post by KillerKelvUK on 2015-07-15
If you were using IGP then yes you'd hit arbitration issues if using seabios however as your using a PCI card for host gfx i think you may be okay.  The only other patch I can think you *could* require is ACS Overide which is about your iommu groupings, the output from the shell script in my first reply will answer that one.

Been reading round some more and found this article [http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html) which actually has a section about multiple devices sharing the same vendor:device id where you want to split the resources between host and guest.  Be worth reading this through to understand how you'd apply it but for now I'd suggest you just get gfx only up and running and worry about audio later.

---

### Post by ipeek90 on 2015-07-16
I'm home and at the machine now.

Currently im running 14.04 with NO patches. I've stubbed out the 7870 VGA only via GRUB.[U][B]

sudo lspci -d 1002: -vvv
[/B][/U]
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Capabilities: [f0] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=0 UnitCnt=20 MastHost- DefDir- DUL-
        Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b+
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency 0: [d]
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD-
        Link Frequency 1: 200MHz
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
        Prefetchable memory behind bridge Upper: 00-00
        Bus Number: 00
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [70] MSI: Enable- Count=1/4 Maskable- 64bit-
        Address: 00000000  Data: 0000

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 72
    Capabilities: [40] Secure device <?>
    Capabilities: [54] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee3f00c  Data: 41b1
    Capabilities: [64] HyperTransport: MSI Mapping Enable+ Fixed+

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #2, PowerLimit 75.000W; Interlock- NoCompl+
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
        DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190 v1] Access Control Services
        ACSCap:    SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
        ACSCtl:    SrcValid+ TransBlk- ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans-
    Kernel driver in use: pcieport

00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #4, PowerLimit 75.000W; Interlock- NoCompl+
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
        DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190 v1] Access Control Services
        ACSCap:    SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
        ACSCtl:    SrcValid+ TransBlk- ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans-
    Kernel driver in use: pcieport

00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #1, Speed 5GT/s, Width x2, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #9, PowerLimit 75.000W; Interlock- NoCompl+
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
        DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190 v1] Access Control Services
        ACSCap:    SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
        ACSCtl:    SrcValid+ TransBlk- ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans-
    Kernel driver in use: pcieport

00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fe700000-fe7fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #2, Speed 5GT/s, Width x2, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #10, PowerLimit 75.000W; Interlock- NoCompl+
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
        DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190 v1] Access Control Services
        ACSCap:    SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
        ACSCtl:    SrcValid+ TransBlk- ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans-
    Kernel driver in use: pcieport

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at f040 [size=8]
    Region 1: I/O ports at f030 [size=4]
    Region 2: I/O ports at f020 [size=8]
    Region 3: I/O ports at f010 [size=4]
    Region 4: I/O ports at f000 [size=16]
    Region 5: Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0 InCfgSpace
    Capabilities: [a4] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at feb0a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at feb09000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at feb08000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at feb07000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: piix4_smbus

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device d693
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: fff00000-000fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at feb06000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe600000-fe6fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot-), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd-
        DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport

00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at feb04000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited / Sapphire Technology Device e241
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at fea00000 (64-bit, non-prefetchable) [size=256K]
    Region 4: I/O ports at e000 [size=256]
    Expansion ROM at fea40000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [270 v1] #19
    Capabilities: [2b0 v1] Address Translation Service (ATS)
        ATSCap:    Invalidate Queue Depth: 00
        ATSCtl:    Enable+, Smallest Translation Unit: 00
    Capabilities: [2c0 v1] #13
    Capabilities: [2d0 v1] #1b
    Kernel driver in use: pci-stub

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: PC Partner Limited / Sapphire Technology Device aab0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 88
    Region 0: Memory at fea60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Kernel driver in use: snd_hda_intel

02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 048b
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 90
    Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at fe900000 (64-bit, non-prefetchable) [size=256K]
    Region 4: I/O ports at d000 [size=256]
    Expansion ROM at fe940000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x8, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [200 v1] #15
    Capabilities: [270 v1] #19
    Kernel driver in use: radeon

02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: ASUSTeK Computer Inc. Device aab0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 89
    Region 0: Memory at fe960000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x8, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Kernel driver in use: snd_hda_intel

```[U][B]


IOMMU.SH


[/B][/U]```
### Group 0 ###
    00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
### Group 1 ###
    00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
### Group 2 ###
    00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
### Group 3 ###
    00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
### Group 4 ###
    00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A)
### Group 5 ###
    00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
### Group 6 ###
    00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
### Group 7 ###
    00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
### Group 8 ###
    00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
### Group 9 ###
    00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
### Group 10 ###
    00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
### Group 11 ###
    00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
### Group 12 ###
    00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
### Group 13 ###
    00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
    06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
### Group 14 ###
    00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
### Group 15 ###
    01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
    01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
### Group 16 ###
    02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240]
    02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
### Group 17 ###
    03:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
### Group 18 ###
    04:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)

```

Quick side question, and I believe I have it correct, but does my /etc/modules file look correct? I change "***kvm_intel" ***to "***kvm_amd"***. Every where I see it, they use the intel version. Not sure if this matters.

```

lp
rtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd

```

Heres some other information...

I can not run the VM without having both VGA and Audi stubbed out.

When I run the VM and it gets past it's boot count down timer... I get the :
```

qemu-system-x86_64: vfio_bar_write(,0xd2ea, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2e9, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2e8, 0x0, 1) failed: Device or resource busy
qemu-system-x86_64: vfio_bar_write(,0xd2ef, 0x0, 1) failed: Device or resource busy

```

And dmesg gives at the exact same time:
```

[   51.428069] vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xd0000000-0xdfffffff 64bit pref]
[   51.428092] vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xd0000000-0xdfffffff 64bit pref]
[   51.428114] vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xd0000000-0xdfffffff 64bit pref]
[   51.428136] vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xd0000000-0xdfffffff 64bit pref]
[   51.456785] vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xd0000000-0xdfffffff 64bit pref]

```

---

### Post by KillerKelvUK on 2015-07-17
Please can you post your guest config so we can see the qemu cmd line or the libvirt xml that is being run.

The details you provide show a good chance of this working i.e the 7870 is in its own iommu group, number 15 which isn't shared with any other device.  The BAR errors I believe refer to base address register which i think are potential arbitration related but I could be wrong.

As for not being able run the guest without VGA and audio being stubbed what is the error message?  Did you remove the audio device from the guest config i.e it was just the 01:00.0 device you passed through?

---

### Post by ipeek90 on 2015-07-17
Sure!

_**Qemu VM Start**_

```

#!/bin/bash

configfile=/etc/vfio-pci1.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-drive file=/home/sezotove/windows.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/sezotove/Downloads/Windows7Pro.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0

```

I did comment it out via # in the above config. It gave this error:

```

vfio: error, group 15 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver

```

Thanks for the help so far!

---

### Post by KillerKelvUK on 2015-07-17
Okay, so you can't pass just 01.00.0 (vga) adapter through unless you also stub out the 01.00.1 (audio) adapter.  Problem is by stubbing the audio adapter using the vendor:device ids (100:aab0) you also stub out the 02.00.1 (audio) adapter for the card you want the host to use. Rock & Hard Place!

The blog I linked earlier mentions a way to address the same vendor:device ids for stubbing pci adapters, but I suggest you keep it simple still and leave that for now.

As a test stub the ids for video and audio, if you're using HDMI audio from the r7 this should break it, if this is what you've effectively been doing and its resulting in the BAR errors I think this is the the arbitration issue which can only be addressed either via OVMF and a UEFI vBIOS on the vga card or by patching the kernel for vga arbitration.  You could look into hacking your 7870 to apply a UEFI vBIOS (vBIOS that supports GOP) but I've little experience here so you need to do homework ([http://www.overclock.net/t/1401987/sapphire-7870-gop-bios#post_20228466](http://www.overclock.net/t/1401987/sapphire-7870-gop-bios#post_20228466)).

Note that by patching the kernel for vga arbitration you effectively limit the graphics capability of the host which kinda invalidates the use of the R7, do you have any integrated gfx on the cpu you could use instead of the r7 for host vga...does you R7 have a UEFI capabily BIOS?

---

### Post by ipeek90 on 2015-07-17
Do you think it would be worth my time or easier for me to return the R7 and purchase an NVIDIA card? 

Am I still looking at vga arbitration issue? If so what are the steps to patching the kernel for that issue. I'd rather not try and hacking of my 7870 if I can help it.

I have been stubbing out both audio and video and getting the BAR errors.

As far as audio goes on the R7, I don't use HDMI. Only DVI/VGA.

---

### Post by KillerKelvUK on 2015-07-18
Don't think replacing the R7 will make anything easier...was thinking it *may* be easier trying to pass the R7 thru instead.  I think the top/bottom of it is the 7870 not having an UEFI vBIOS means that patching for vga arbitraion is the only way to go, if you want to pass thru the 7870.  One of the forum members called reger has posted a thread on passthrough...in fact its probably the thread you've followed looking at your setup.  In their he posts some kernel patches and a guide (or links to one), best to have a look at that and start up a new thread if you get stuck.

---

### Post by ipeek90 on 2015-07-25
So I've tried the kernel patches to the best of my ability and still get the same issues. I guess I'll just pass on this dream for now. Thanks for the help.

---

### Post by redger on 2015-07-25
you shouldn't need any patches on the 14.04 kernel. I run GPU passthrough with an unpatched kernel, though I'm currently using UEFI passthrough, which I recommend.
For UEFI based passthrough your grpahics card will need a UEFI Bios. You can construct one of these easily enough, I created one for my HD6950 using the instructions here
[http://www.insanelymac.com/forum/top...any-ati-cards/]("http://www.insanelymac.com/forum/top...any-ati-cards/")
[http://www.overclock.net/t/1474306/r...fi-bios-thread]("http://www.overclock.net/t/1474306/r...fi-bios-thread")

If UEFI doesn't suit or doesn't work there should be no problems with SeaBios based passthrough given that you have an AMD motherboard and AMD graphics cards

Rather than using direct commands and the Q35 motherboard, you'd be better to use VirtManager and the standard i440fx motherboard (virt-manager default). Life will be much easier

It looks as though your motherboard has "good ACS/IOMMU separation" so no need for an ACS patch

It will be necessary to isolate the sound sections of the 2 video cards so that one is allocated to the stub and the other isn't. Perhaps a read of the blog Kelv pointed to above 
[http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html]("http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html")
You would need to either upgrade to kernel 3.16 or later or use xen-pciback (probably preferred since it's a standard component so no need ot customer kernels / patches etc)

Virt-manager will do all the locks and transfers for you so there's no need for a vfio-bind script.

Stick with the process, it's worth it once the initial learning curve is mastered :)

---

### Post by ipeek90 on 2015-07-25
> **redger said:**
> you shouldn't need any patches on the 14.04 kernel. I run GPU passthrough with an unpatched kernel, though I'm currently using UEFI passthrough, which I recommend.
For UEFI based passthrough your grpahics card will need a UEFI Bios. You can construct one of these easily enough, I created one for my HD6950 using the instructions here
[http://www.insanelymac.com/forum/top...any-ati-cards/](http://www.insanelymac.com/forum/top...any-ati-cards/)
[http://www.overclock.net/t/1474306/r...fi-bios-thread](http://www.overclock.net/t/1474306/r...fi-bios-thread)

If UEFI doesn't suit or doesn't work there should be no problems with SeaBios based passthrough given that you have an AMD motherboard and AMD graphics cards

Rather than using direct commands and the Q35 motherboard, you'd be better to use VirtManager and the standard i440fx motherboard (virt-manager default). Life will be much easier

It looks as though your motherboard has "good ACS/IOMMU separation" so no need for an ACS patch

It will be necessary to isolate the sound sections of the 2 video cards so that one is allocated to the stub and the other isn't. Perhaps a read of the blog Kelv pointed to above 
[http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html)
You would need to either upgrade to kernel 3.16 or later or use xen-pciback (probably preferred since it's a standard component so no need ot customer kernels / patches etc)

Virt-manager will do all the locks and transfers for you so there's no need for a vfio-bind script.

Stick with the process, it's worth it once the initial learning curve is mastered :)

I'm willing to give the UEFI a try but I've looked over the threads and they're so confusing. I am still willing to give it a shot.

If I don't need the ACS patch with SeaBIOS, what would cause the issue I'm having? Is it the Q35 Motherboard setting? Or is it that the sound sections are causing some issue that is not allowing the card to be completely stubbed out? I also looked at the vfio.blockspot.co.uk post on using virt-manager and found it completely confusing and my version was missing options or they were placed in different locations.

Thanks for the vote of confidence.

---

### Post by redger on 2015-07-26
Have a look at this post ...
[http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460")

It's the record I entered after having successfully created a UEFI ROM for a Sapphire 6950

---

### Post by redger on 2015-07-26
PS you will still need to use xen-pciback to grab the card during boot - before the host driver grabs it

---

### Post by ipeek90 on 2015-07-26
> **redger said:**
> Have a look at this post ...
[http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460](http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460)

It's the record I entered after having successfully created a UEFI ROM for a Sapphire 6950

I've got an XP vm up and I've downloaded the atiwinflash from here [http://www.techpowerup.com/downloads/2311/ati-winflash-2-6-7/mirrors](http://www.techpowerup.com/downloads/2311/ati-winflash-2-6-7/mirrors)

No idea how to use it from there. When I run the ATIWinFlash it errors out not finding a video card and I have no clue how to use the cli version of it.

Any tips?

> **ipeek90 said:**
> I've got an XP vm up and I've downloaded the atiwinflash from here [http://www.techpowerup.com/downloads/2311/ati-winflash-2-6-7/mirrors](http://www.techpowerup.com/downloads/2311/ati-winflash-2-6-7/mirrors)

No idea how to use it from there. When I run the ATIWinFlash it errors out not finding a video card and I have no clue how to use the cli version of it.

Any tips?

Scratch that...

I see there is a ZIP to download [https://www.dropbox.com/s/5bphx05ma8z9n13/AMD-UEFI-GOP-MAKER.zip](https://www.dropbox.com/s/5bphx05ma8z9n13/AMD-UEFI-GOP-MAKER.zip)

Then moving the vbios from your comment on the overclockers thread. Though I'm getting the following output when running the .command script.:

```

./UEFI_ROM.command: line 7: PWD: command not found
orig size - 65536
57344+0 records in
57344+0 records out
57344 bytes (57 kB) copied, 0.130163 s, 441 kB/s
Before:
OpRom (size=65536, indicator_offset=0x22d, indicator=0x80, checksum=0x0)
OpRom (size=57344, indicator_offset=0x31, indicator=0x80, checksum=0xc7)

After:
OpRom (size=65536, indicator_offset=0x22d, indicator=0x0, checksum=0x80)
OpRom (size=57344, indicator_offset=0x31, indicator=0x80, checksum=0xc7)
Your 'new' UEFI rom is ready at uefi.rom


```

Looks like all is fine, it's just failing on PWD rather than pwd?

I also see I need to run the atiflash -p 0 uefi.rom

That correct?

I did the flash.. I think. I don't actually think it worked. I booted to a FreeDOS CD and when using the LiveCD option it gives me "Adapter not found" After changing this to LiveCd with the other options I run atiflash -i to list my adapters and my computer reboots. Even after running atiflash -p 0 romname.rom It does the same.

Still have not gotten the UEFI to work. However!!!!!!! I went and returned the R7 for a GTX 750 and have blacklisted the AMD card. 


I tried to run my VM via CLI with SeaBios and I get the following:

```

qemu: could not load PC BIOS '/usr/share/qemu/bios.bin'

```


Here is some output from dmesg when running the vm via Virt-Manager:

```

[ 2244.172650] systemd-hostnamed[7576]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2475.165967] device vnet0 entered promiscuous mode
[ 2475.186212] virbr0: port 1(vnet0) entered listening state
[ 2475.186239] virbr0: port 1(vnet0) entered listening state
[ 2477.192829] virbr0: port 1(vnet0) entered learning state
[ 2477.378214] vfio-pci 0000:01:00.0: enabling device (0400 -> 0403)
[ 2477.409328] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
[ 2477.409341] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1b@0x2d0
[ 2477.414130] vfio-pci 0000:01:00.1: enabling device (0400 -> 0402)
[ 2479.199795] virbr0: topology change detected, propagating
[ 2479.199808] virbr0: port 1(vnet0) entered forwarding state
[ 2479.690850] kvm: zapping shadow pages for mmio generation wraparound
[ 2836.443457] virbr0: port 1(vnet0) entered disabled state
[ 2836.444856] device vnet0 left promiscuous mode
[ 2836.444875] virbr0: port 1(vnet0) entered disabled state
[ 2837.699080] device vnet0 entered promiscuous mode
[ 2837.715139] virbr0: port 1(vnet0) entered listening state
[ 2837.715191] virbr0: port 1(vnet0) entered listening state
[ 2839.721790] virbr0: port 1(vnet0) entered learning state
[ 2840.461221] vfio-pci 0000:01:00.0: enabling device (0400 -> 0403)
[ 2840.491145] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
[ 2840.491159] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1b@0x2d0
[ 2840.495723] vfio-pci 0000:01:00.1: enabling device (0400 -> 0402)
[ 2841.728804] virbr0: topology change detected, propagating
[ 2841.728818] virbr0: port 1(vnet0) entered forwarding state
[ 2842.639889] kvm: zapping shadow pages for mmio generation wraparound
[ 2900.720279] usb 7-4: new full-speed USB device number 2 using ohci-pci
[ 2900.888558] usb 7-4: New USB device found, idVendor=1532, idProduct=0502
[ 2900.888567] usb 7-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2900.888572] usb 7-4: Product: Razer Kraken USB
[ 2900.888576] usb 7-4: Manufacturer: Razer
[ 2900.985874] input: Razer Razer Kraken USB as /devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.3/0003:1532:0502.0004/input/input21
[ 2900.986168] hid-generic 0003:1532:0502.0004: input,hidraw3: USB HID v1.00 Device [Razer Razer Kraken USB] on usb-0000:00:16.0-4/input3
[ 3014.529122] virbr0: port 1(vnet0) entered disabled state
[ 3014.531367] device vnet0 left promiscuous mode
[ 3014.531406] virbr0: port 1(vnet0) entered disabled state
[ 3015.186076] device vnet0 entered promiscuous mode
[ 3015.202064] virbr0: port 1(vnet0) entered listening state
[ 3015.202100] virbr0: port 1(vnet0) entered listening state
[ 3016.971074] vfio-pci 0000:01:00.0: enabling device (0400 -> 0403)
[ 3017.000644] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
[ 3017.000659] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1b@0x2d0
[ 3017.005817] vfio-pci 0000:01:00.1: enabling device (0400 -> 0402)
[ 3017.208697] virbr0: port 1(vnet0) entered learning state
[ 3019.215686] virbr0: topology change detected, propagating
[ 3019.215699] virbr0: port 1(vnet0) entered forwarding state
[ 3019.351142] kvm: zapping shadow pages for mmio generation wraparound
[ 3083.473122] retire_capture_urb: 2 callbacks suppressed
[ 3094.576097] retire_capture_urb: 13 callbacks suppressed



```

After using Virt-Manager to setup a new VM and using it to passthrough the PCI I get windows installed and I get the following in the Device Manager:

[IMG]http://i.imgur.com/RCKG0J9.png[/IMG]

And when I try and install the Catalyst drivers:

[IMG]http://i.imgur.com/c6Jszxk.png[/IMG]

Any ideas?

Okay....

Now I've gotten it up and running. I've passed through the 7870 and installed windows all from using the start script.

I've gotten the drivers installed and it's all being recognized. 

The only thing I'm working on now is the bridged network. When creating the VM in the Virt-Manager the bridge network works just fine. I can VNC to it etc.. But when creating it via the script it seems to assign it an IP address similar to my network settings. 

My network uses 10.0.1.x with a gateway of 10.0.1.1

It's being assigned 10.0.2.x with a gateway of 10.0.2.2

The virbr0 device is 

```

virbr0    Link encap:Ethernet  HWaddr fa:a3:9f:e4:b0:c3  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by redger on 2015-07-28
not an expert in this area, and haven't had problems with Qemu. I did have to establish a new bridge in order to provide an on-network address for an LXC VM (running HTPC services)... pretty easy and works well.

try this ..... [https://bbs.archlinux.org/viewtopic.php?id=182320]("https://bbs.archlinux.org/viewtopic.php?id=182320")  see if his approach helps  (not something I've had problems with)

You may also want to check
[LIST]
[*]/etc/qemu-ifup
[*]/etc/netconfig
[*]/etc/libivrt/qemu/networks/default.xml
[/LIST]

fwiw I created this entry in /etc/networks/interfaces for the LXC VM which needed to be available to my home network
```
auto rebr0
iface rebr0 inet static
        address 192.168.0.xx
        netmask 255.255.255.0 
        gateway 192.168.0.xx
        dns-nameservers 31.3.xx.xx
        bridge_ports eth1
        bridge_stp off
```

where xx = some appropriate numbers :)

---

### Post by ipeek90 on 2015-07-30
I've figured out what is causing the 10.0.2.2 gateway and IP... I had installed VirtualBox and it's somehow forcing my VM to use these settings. I've purged VirtualBox like it was last nights dinner and I'm bulimic....But still my VM keeps getting that address.

Any clue where I might be missing a file or some setting that is still allowing this?

Just wanted to report back and thank you guys for the help. I've gotten it all working. Will be writing a block post and linking it here when I'm done with all the information I've gathered.

Thanks a TON!

---

### Post by marthamarhta on 2015-08-03
I have just successfully set up KVM passthrough with my GTX 750TI.
I patched the 3.18.0 Kernel with ACS / i915 and followed this guide:[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768).
The Virtual Machine uses Windows 10 and works flawlessly.
Now  I wanted to take it one step further and use remastersys, in order  to  create a Live CD of that system, to be able to run such gpu passed   Virtual Machines from a Live CD. (Actually they would run from RAM, as I   use the toram paramater to boot)
After creating and booting the LiveCD, I get the following error when I run the script, that initiates the virtual machine:
```
 
vfio: error no iommu_group for device

```I have realized, that remastersys does not include the grub.cfg  in /boot/grub/grub.cfg , since it uses isolinux as a bootloader.
This could be the reason for the problem, seeing as the error code relates to the iommu parameters missing in the boot config.
Is there a way around using the grub.cfg, while getting the passthrough working?
Or does anyone know how to force remastersys to use grub with my grub.cfg instead of isolinux?

Thanks!

---

### Post by KillerKelvUK on 2015-08-03
> **marthamarhta said:**
> I have just successfully set up KVM passthrough with my GTX 750TI.
I patched the 3.18.0 Kernel with ACS / i915 and followed this guide:[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768).
The Virtual Machine uses Windows 10 and works flawlessly.
Now  I wanted to take it one step further and use remastersys, in order  to  create a Live CD of that system, to be able to run such gpu passed   Virtual Machines from a Live CD. (Actually they would run from RAM, as I   use the toram paramater to boot)
After creating and booting the LiveCD, I get the following error when I run the script, that initiates the virtual machine:
```
 
vfio: error no iommu_group for device

```I have realized, that remastersys does not include the grub.cfg  in /boot/grub/grub.cfg , since it uses isolinux as a bootloader.
This could be the reason for the problem, seeing as the error code relates to the iommu parameters missing in the boot config.
Is there a way around using the grub.cfg, while getting the passthrough working?
Or does anyone know how to force remastersys to use grub with my grub.cfg instead of isolinux?

Thanks!

I'd expect a config file for isolinux similar to the grub where you can specify kernel parameters...something like an isolinux.cfg file? ([http://www.syslinux.org/wiki/index.php/Isolinux.cfg](http://www.syslinux.org/wiki/index.php/Isolinux.cfg))

---

### Post by marthamarhta on 2015-08-03
> **KillerKelvUK said:**
> I'd expect a config file for isolinux  similar to the grub where you can specify kernel parameters...something  like an isolinux.cfg file? ([http://www.syslinux.org/wiki/index.php/Isolinux.cfg](http://www.syslinux.org/wiki/index.php/Isolinux.cfg))


You are right! 

In /etc/remastersys/isolinux/ there is a file called isolinux.cfg.vesamenu , which holds the boot paramaters for the liveboot.
```
default vesamenu.c32
prompt 0
timeout 100

menu title __LIVECDLABEL__
menu background splash.png
menu color title 1;37;44 #c0ffffff #00000000 std

label live
  menu label live - boot the Live System
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label xforcevesa
  menu label xforcevesa - boot Live in safe graphics mode
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --

label install
  menu label install - start the installer directly
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

label memtest
  menu label memtest - Run memtest
  kernel /install/memtest
  append -

label hd
  menu label hd - boot the first hard disk
  localboot 0x80
  append -


```

Now how, or rather, where would I have to add what parameters?

In order to get KVM Passthrough to work I normally have to add the following to /etc/default/grub:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1**"
GRUB_CMDLINE_LINUX=""
```

Which is then updated to the /boot/grub/grub.cfg via ```
sudo update-grub
```

I am not sure what needs to be added where, to the isolinux.conf

---

### Post by KillerKelvUK on 2015-08-03
So on your host machine you're creating the live cd from you run...

```

cat /proc/cmdline

```

you see the entire boot line kernel and parameters that were run on your system at start up, this is the result of your updates to grub and the update-grub command

...isolinux has a varient of this as it loads the KERNEL file and then APPEND's the boot arguments/parameters...it would be in the 'append' line you need to add your additional kernel parameters I believe.

---

### Post by marthamarhta on 2015-08-03
Thanks for your help, I managed to get it working, thanks to your previous suggestion.
I modified the boot parameters of the isolinux.conf file for a life boot, adding the line that I would normally update the grub.cfg with.
I also added toram at the end, which moves the entire Live System to RAM, resulting in my Windows Virtual Machine to have crazy read and write speeds, since the img file is also in RAM.
```
label live
  menu label live - boot the Live System
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash **intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1 toram** --
```

Thank you very much, you are awesome.):P

---

### Post by njuman on 2015-12-22
> **ipeek90 said:**
> Okay....

Now I've gotten it up and running. I've passed through the 7870 and installed windows all from using the start script.

I've gotten the drivers installed and it's all being recognized. 

The only thing I'm working on now is the bridged network. When creating the VM in the Virt-Manager the bridge network works just fine. I can VNC to it etc.. But when creating it via the script it seems to assign it an IP address similar to my network settings. 

My network uses 10.0.1.x with a gateway of 10.0.1.1

It's being assigned 10.0.2.x with a gateway of 10.0.2.2

The virbr0 device is 

```

virbr0    Link encap:Ethernet  HWaddr fa:a3:9f:e4:b0:c3  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Hi, did  you passtrough your vga in the first slot? if so how did you do   that. I can not pass through my vga in the first slot, only the second   one allows me to do that.

---

### Post by ipeek90 on 2015-12-22
I replied to your PM but just for good measure I've documented my process at [http://peektech.net/?p=236](http://peektech.net/?p=236)

Good luck!

---

### Post by njuman on 2015-12-23
Could somebody help me? My specs (passthrough works fine):
```
Ubuntu 14.04.3 no patches, kernel 3.19 latest via software updater.
MOBO: Gigabyte GA970-DS3P (bios does not allow to change which vga to start)
AMD Athlon II 640 X4
GPU1 first slot (host) Ati HD4650
GPU2 second slot (guest) GTX 650
RAM 8GB
Guest OS - Win 8.1
```
The problem is i can not swith around my vga cards and passthough GTX in the first slot.
Here is what i have been tried to do:
Case 1: GTX pci-stubed, nouveau is not blacklisted - i can see display   output on both the vga's in dual monitor mode. Launching qemu hang the   system
Case 2: GTX pci-stubed, nouveau is blacklisted - on GTX i see window   "your system is running in low graphics mode" and there is no chance to get   to the X (logon, desktop e.g.). On the HD4650 - black screen.

---

### Post by njuman on 2016-01-21
I'm now able to run ubuntu on the second slot vga, using xorg.conf, qemu runs with no errors, but there is still no video output from the first vga slot...

---

