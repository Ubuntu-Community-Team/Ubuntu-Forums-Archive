---
title: "UbuStu 9.10 64 - Audiofire12 issues..."
date: 2010-01-16
forum: Ubuntu Studio
---

### Post by tlstudio on 2010-01-16
Hello! Although this is my first post in the ubuntu community I have been using ubuntu studio for a few years now and I have to say I'm very impressed with the quality of work that is put into each release.

Having said that I do have an issue with my new audio interface, an Echo Audiofire12 (upgraded from an M-Audio Delta 1010), for which I'm hoping to find a solution. I'm getting xruns and glitchy audio (distorted output, haven't tried recording yet) and at times jack will "timeout" and stop or terminate with an exit code. Note that I'm running a fresh install of UbuStu 9.10 64, I've checked all the options in Ubuntu Studio Controls, added the recommended lines to limits.conf and added myself to the video group to access the raw1394 device.

First of all here is the lspci -vv for my pci-e firewire card (VIA VT6330):
```
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 (prog-if 10)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f9000000 (64-bit, non-prefetchable) [size=2K]
    Region 2: I/O ports at a000 [size=256]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [80] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [98] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <2us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [130] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
```Should the firewire card be using the raw1394 driver?

Here is an excerpt from the qjackctl log that caught my eye
```
17:00:53.013 /usr/bin/jackd -R -p128 -dfirewire -r96000 -p128 -n3
01257100645:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
01257769586: [31mError (fireworks_session_block.cpp)[ 129] loadFromDevice: Flash read failed
```Which device is it failing to read, the Audiofire or the firewire card? Could this be a result of the Audiofire firmware being too "new"? I have the latest version installed - v5.5 I believe, does anyone else have it working with this version?

dmesg | grep 1394
```
[    1.979309] ohci1394 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.979316] ohci1394 0000:03:00.0: setting latency timer to 64
[    2.034098] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[f9000000-f90007ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    2.040118] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    3.297359] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[ff00000000000000]
[    3.298728] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[001486045b6575de]
[   13.318291] ieee1394: raw1394: /dev/raw1394 device initialized
```What's up with the "suspicious values" line, again is this referring to the Audiofire or the firewire card? It looks to me like the firewire card is "suspicious" and the Audiofire is the Node added a couple lines down. I'm beginning to think the issue might be the firewire card...

And here are the ffado test results

ffado-test ListDevices
```
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0xff00000000000000  0x00FF0000  0x00000000   Linux - ohci1394  - 
   1       0x001486045b6575de  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
no message buffer overruns
```ffado-test Discover
```
01768620715: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
01768630391: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768631923: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768633391: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768634689: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768636235: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768705918: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768707390: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768709279: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768710914: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768712366: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
01768771021: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
01768771045: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0xFFFF804800001486)
01768771051: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0xFFFF80480000AF12)
01768771062: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
01768771066: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
01768771075: Debug (Configuration.cpp)[ 185] showSetting:     driver = 140733193388034 (0x7FB700000002)
01768771079: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
01768771085: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 140733193388034 (0x7FB700000002)
01768771137: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
01768771148: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
01768771152: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
01768771158: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
01768771161: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
01768771166: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
01768771170: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
01768771175: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
01768771289: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
01768771334: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
01768771340: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
01768771348: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
01768771351: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
01768771357: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
01768771360: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
01768771365: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
01768771368: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
01768772849: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
01768772855: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
01768773202: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01768773208: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (1,1,0,0,0)
01768773871: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01768773876: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (1,1,0,1,0)
01768774517: Debug (avc_musicsubunit.cpp)[  65] discover: Discovering MusicSubunit...
01768774530: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
01768783328: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
01768783698: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
01768783710: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
01768783713: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 2
01768783718: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
01768783723: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
01768784148: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768784155: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,0)
01768784481: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
01768784488: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
01768784886: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768784892: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,0)
01768785433: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
01768785446: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
01768785943: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768785951: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,0)
01768786412: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01768786719: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768786730: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,1)
01768787020: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01768787031: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
01768787384: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768787396: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,0)
01768787705: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01768788073: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
01768788080: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,1)
01768788390: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01768788434: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
01768788762: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
01768789385: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
01768789691: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
01768791026: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
01768791037: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
01768791040: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
01768791044: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
01768791381: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
01768791391: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
01768791398: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
01768791406: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
01768791409: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01768791417: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01768791421: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01768791427: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01769294476: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01769294535: Error (fireworks_device.cpp)[ 216] doEfcOverAVC: EfcOverAVCCmd command failed
01769294545: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 8
01769294551: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01769294553: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01769294558: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000008
01769294560: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000001
01769294565: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01769294567: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000007
01769294571: Debug (efc_cmds_flash.cpp)[ 121] showEfcCmd: EFC Flash Read:
01769294573: Debug (efc_cmds_flash.cpp)[ 122] showEfcCmd:  Address           : 17179901952
01769294577: Debug (efc_cmds_flash.cpp)[ 123] showEfcCmd:  Length (quadlets) : 17179869248
01769294580: Debug (efc_cmds_flash.cpp)[ 124] showEfcCmd:  Data              : 
01769294585: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294587: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294593: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294595: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294600: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294602: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294606: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294608: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294612: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294614: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294618: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294620: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294625: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294627: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294631: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294633: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294637: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294639: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294645: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294647: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294651: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294653: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294658: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294660: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294664: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294666: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294670: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294672: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294676: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294678: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294683: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294684: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294689: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294691: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294698: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294700: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294704: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294706: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294710: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294712: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294717: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294719: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294723: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294725: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294730: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294732: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294736: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294738: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294742: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294744: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294750: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294752: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294756: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294758: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294762: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294764: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294769: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294771: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294775: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294777: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294781: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294783: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294818: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294821: Debug (efc_cmds_flash.cpp)[ 126] showEfcCmd:                      00000000 
01769294827: Error (fireworks_device.cpp)[ 737] readFlash: Flash read failed for block 0x00008000 (64 quadlets)
01769294830: Error (fireworks_session_block.cpp)[ 129] loadFromDevice: Flash read failed
01769294838: Error (fireworks_device.cpp)[ 426] loadSession: Could not load session block
01769294841: Warning (fireworks_device.cpp)[ 366] buildMixer: Could not load session
01769294856: Debug (devicemanager.cpp)[ 631] discover: discovery of node 1 on port 0 done...
01769294860: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
01769294885: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
01769294889: Debug (Element.cpp)[ 121] show: Element DeviceManager
01769294895: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
01769294910: Debug (devicemanager.cpp)[1202] showDeviceInfo: --- Device  0 ---
01769294913: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01769294917: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01769294920: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01769294924: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000002
01769294926: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000000
01769294933: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000000
01769294935: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01769294940: Debug (efc_cmds_hardware.cpp)[ 127] showEfcCmd: EFC HW CAPS info:
01769294942: Debug (efc_cmds_hardware.cpp)[ 128] showEfcCmd:  Flags   : 0x00000111
01769294947: Debug (efc_cmds_hardware.cpp)[ 129] showEfcCmd:  GUID    : 001486045B6575DE
01769294950: Debug (efc_cmds_hardware.cpp)[ 130] showEfcCmd:  HwType  : 0x0000AF12
01769294955: Debug (efc_cmds_hardware.cpp)[ 131] showEfcCmd:  Version : 5776851272204288
01769294957: Debug (efc_cmds_hardware.cpp)[ 132] showEfcCmd:  Vendor  : Echo Digital Audio
01769294962: Debug (efc_cmds_hardware.cpp)[ 133] showEfcCmd:  Model   : AudioFire12
01769294964: Debug (efc_cmds_hardware.cpp)[ 135] showEfcCmd:  Supported Clocks   : 0x00000005
01769294970: Debug (efc_cmds_hardware.cpp)[ 136] showEfcCmd:  # 1394 Playback    : 12
01769294972: Debug (efc_cmds_hardware.cpp)[ 137] showEfcCmd:  # 1394 Record      : 12
01769294977: Debug (efc_cmds_hardware.cpp)[ 138] showEfcCmd:  # Physical out     : 12
01769294979: Debug (efc_cmds_hardware.cpp)[ 139] showEfcCmd:  # Physical in      : 12
01769294983: Debug (efc_cmds_hardware.cpp)[ 142] showEfcCmd:  # Output Groups    : 1
01769294986: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 0: Type 0x00, count 12
01769294992: Debug (efc_cmds_hardware.cpp)[ 147] showEfcCmd:  # Input Groups     : 1
01769294994: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 0: Type 0x00, count 12
01769294999: Debug (efc_cmds_hardware.cpp)[ 152] showEfcCmd:  # Midi out         : 1
01769295017: Debug (efc_cmds_hardware.cpp)[ 153] showEfcCmd:  # Midi in          : 1
01769295022: Debug (efc_cmds_hardware.cpp)[ 154] showEfcCmd:  Max Sample Rate    : 96000
01769295025: Debug (efc_cmds_hardware.cpp)[ 155] showEfcCmd:  Min Sample Rate    : 32000
01769295030: Debug (efc_cmds_hardware.cpp)[ 156] showEfcCmd:  DSP version        : 0x05050000
01769295032: Debug (efc_cmds_hardware.cpp)[ 157] showEfcCmd:  ARM version        : 0x05050000
01769295036: Debug (efc_cmds_hardware.cpp)[ 158] showEfcCmd:  # Mix play chann.  : 12
01769295039: Debug (efc_cmds_hardware.cpp)[ 159] showEfcCmd:  # Mix rec chann.   : 12
01769295046: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
01769295048: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 1
01769295053: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Echo Digital Audio
01769295056: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: AudioFire12
01769295063: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 001486045b6575de
01769295068: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev0
01769295118: Debug (devicemanager.cpp)[1205] showDeviceInfo: Clock sync sources:
01769802778: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01769802835: Error (fireworks_device.cpp)[ 216] doEfcOverAVC: EfcOverAVCCmd command failed
01769802841: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01769802847: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01769802850: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01769802854: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000000A
01769802857: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01769802861: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01769802863: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000007
01769802867: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01769802870: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 140737488355327
01769802874: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 140737488355327
01769802877: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 140733193388032
01769802882: Error (fireworks_device.cpp)[ 623] getClock: Could not get clock info
01769805311: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: Internal          , Id:  0, Valid: 1, Active: 0, Locked 1, Slipping: 0, Description: Internal sync
01769805324: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: WordClock         , Id:  2, Valid: 0, Active: 0, Locked 1, Slipping: 0, Description: Word Clock
no message buffer overruns

```Lots of failed this and that in the last one. Definitely seems like a communication issue of some sort. The question is, is it the Audiofire or the firewire card?

Does anyone have a magical solution for me? :D

Or a confirmation that I need to find a new firewire card? Or even just some ideas?

Thanks!

TLStudio

---

### Post by AutoStatic on 2010-01-16
Hello TLStudio, The Audiofire 12 is [fully supported]("http://ffado.org/?q=node/71") so that shouldn't be the issue though. It might be the firmware you're using, so maybe you could try a newer version of FFADO. Another option I would consider in your case is to get yourself a Firewire card that is more suited for audio processing, like a Belkin card with a Texas Instruments chipset.
And your question if the info concerns your Firewire card or the Audiofire, all ffado related info is about your Audiofire and I think the rest also. It seems as if the FFADO driver has difficulties reading your device, so I think the first option I pointed out would be worth a try. Not sure though if there's a PPA with a newer version of FFADO, you might have to compile it yourself.

---

### Post by trulan on 2010-01-16
I would definitely try updating you rtirq script and adding the settings to it to prioritize your firewire card's irq.  (You are running the real time kernel, correct?)

See this thread:
[http://ubuntuforums.org/showthread.php?t=1328175](http://ubuntuforums.org/showthread.php?t=1328175)
especially posts one and five.

---

### Post by AutoStatic on 2010-01-16
Yup, I would try that first too.

---

### Post by tlstudio on 2010-01-18
Ok, so I downgraded the firmware on the AF12 to 4.8 and the "flash read failed" message in qjackctl is now gone as are many of the errors in ffado-test Discover. This did nothing to help the performance issues however. I followed the thread posted (thanks trulan!) and applied the changes to rtirq which "seemed" to have no effect (yes I am running RT kernel).

However I then checked the cpu frequency scaling app also as indicated in the thread and lo and behold all cpu cores (it's a quad core) were set to "on demand"! So I set them all to "performance" and incredibly my performance problems vanished, I was able to set my frames to the lowest setting of 16 without xruns! qjackctl reports 0.5ms while ardour reports 0.2ms! I don't doubt the rtirq changes optimized this result. This leads me to believe I've had this problem since 8.04 - my lowest reliable frame setting with the Delta1010 was 256 - and the fact that I switched to firewire just brought the problem to light because of the extra processing/latency/whatnot. I always wondered why I wasn't able to achieve the super low latency reported by others.

So the only problem now is making that "performance" setting stick. It does not persist through reboots for me. I'll try the script provided in the referenced thread (thanks again trulan!) and report back.

Here is the new ffado-test Discover, are these messages "normal"?
```
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00948893965: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00948901052: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948902244: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948903543: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948904820: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948905992: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948965274: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948966533: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948967860: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948969121: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00948970377: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00949023951: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00949023979: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0xFFFF808400001486)
00949023984: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0xFFFF80840000AF12)
00949023991: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00949023995: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00949024001: Debug (Configuration.cpp)[ 185] showSetting:     driver = 140733193388034 (0x7F7B00000002)
00949024004: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00949024012: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 140733193388034 (0x7F7B00000002)
00949024053: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00949024059: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00949024063: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00949024068: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00949024072: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00949024077: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00949024080: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00949024085: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00949024201: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
00949024241: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00949024245: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00949024398: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00949024404: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00949024410: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00949024413: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00949024419: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00949024422: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00949026444: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
00949026453: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00949026731: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00949026738: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
00949027437: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00949027444: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
00949028245: Debug (avc_musicsubunit.cpp)[  65] discover: Discovering MusicSubunit...
00949028252: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00949040572: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00949040851: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
00949040860: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
00949040879: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 2
00949040886: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
00949040891: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
00949041425: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949041432: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,0)
00949041852: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
00949041858: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
00949042416: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949042425: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,0)
00949043295: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
00949043303: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
00949043722: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949043729: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,0)
00949044191: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00949044574: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949044584: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,1)
00949044856: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00949044882: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
00949045433: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949045444: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,0)
00949045846: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00949046362: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00949046451: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,1)
00949046847: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00949046853: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
00949047216: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
00949047933: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00949048369: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00949049961: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
00949049971: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
00949049974: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
00949049980: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
00949050424: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
00949050434: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
00949050440: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
00949050448: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
00949050451: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00949050461: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00949050464: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00949050471: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00949094864: Debug (devicemanager.cpp)[ 631] discover: discovery of node 0 on port 0 done...
00949094876: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00949094901: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
00949094911: Debug (Element.cpp)[ 121] show: Element DeviceManager
00949094914: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00949094928: Debug (devicemanager.cpp)[1202] showDeviceInfo: --- Device  0 ---
00949094934: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00949094936: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00949094940: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00949094942: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000002
00949094947: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000000
00949094948: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000000
00949094954: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00949094956: Debug (efc_cmds_hardware.cpp)[ 127] showEfcCmd: EFC HW CAPS info:
00949094960: Debug (efc_cmds_hardware.cpp)[ 128] showEfcCmd:  Flags   : 0x00000011
00949094963: Debug (efc_cmds_hardware.cpp)[ 129] showEfcCmd:  GUID    : 001486045B6575DE
00949094986: Debug (efc_cmds_hardware.cpp)[ 130] showEfcCmd:  HwType  : 0x0000AF12
00949094989: Debug (efc_cmds_hardware.cpp)[ 131] showEfcCmd:  Version : 5776851272204288
00949094993: Debug (efc_cmds_hardware.cpp)[ 132] showEfcCmd:  Vendor  : Echo Digital Audio
00949094996: Debug (efc_cmds_hardware.cpp)[ 133] showEfcCmd:  Model   : AudioFire12
00949095009: Debug (efc_cmds_hardware.cpp)[ 135] showEfcCmd:  Supported Clocks   : 0x00000005
00949095012: Debug (efc_cmds_hardware.cpp)[ 136] showEfcCmd:  # 1394 Playback    : 12
00949095017: Debug (efc_cmds_hardware.cpp)[ 137] showEfcCmd:  # 1394 Record      : 12
00949095019: Debug (efc_cmds_hardware.cpp)[ 138] showEfcCmd:  # Physical out     : 12
00949095023: Debug (efc_cmds_hardware.cpp)[ 139] showEfcCmd:  # Physical in      : 12
00949095025: Debug (efc_cmds_hardware.cpp)[ 142] showEfcCmd:  # Output Groups    : 1
00949095033: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 0: Type 0x00, count 12
00949095035: Debug (efc_cmds_hardware.cpp)[ 147] showEfcCmd:  # Input Groups     : 1
00949095041: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 0: Type 0x00, count 12
00949095044: Debug (efc_cmds_hardware.cpp)[ 152] showEfcCmd:  # Midi out         : 1
00949095048: Debug (efc_cmds_hardware.cpp)[ 153] showEfcCmd:  # Midi in          : 1
00949095050: Debug (efc_cmds_hardware.cpp)[ 154] showEfcCmd:  Max Sample Rate    : 192000
00949095054: Debug (efc_cmds_hardware.cpp)[ 155] showEfcCmd:  Min Sample Rate    : 32000
00949095056: Debug (efc_cmds_hardware.cpp)[ 156] showEfcCmd:  DSP version        : 0x04080000
00949095061: Debug (efc_cmds_hardware.cpp)[ 157] showEfcCmd:  ARM version        : 0x04080000
00949095063: Debug (efc_cmds_hardware.cpp)[ 158] showEfcCmd:  # Mix play chann.  : 12
00949095067: Debug (efc_cmds_hardware.cpp)[ 159] showEfcCmd:  # Mix rec chann.   : 12
00949095071: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
00949095077: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 0
00949095079: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Echo Digital Audio
00949095083: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: AudioFire12
00949095088: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 001486045b6575de
00949095094: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev0
00949095136: Debug (devicemanager.cpp)[1205] showDeviceInfo: Clock sync sources:
00949095589: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00949095596: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00949095620: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00949095623: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000072
00949095628: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
00949095630: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
00949095634: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00949095637: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
00949095641: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 140733193388032
00949095643: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 140733193484032
00949095648: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 140733193388032
00949097620: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: Internal          , Id:  0, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal sync
00949097632: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: WordClock         , Id:  2, Valid: 0, Active: 0, Locked 1, Slipping: 0, Description: Word Clock
no message buffer overruns
```Thanks!

TLStudio

---

### Post by AutoStatic on 2010-01-19
Good to read that it works! You could try disabling the ondemand service alltogether. This can be done with the **sysv-rc-conf** tool or with BUM (BootUp Manager), both available in Synaptic. On my desktop I disabled the ondemand service, on my notebook I use the script as provided in aforementioned rtirq thread because I still like to use the ondemand service when the notebook is running on batteries.
And your ffado-test Discover output looks ok to me, but I'm not a FFADO expert.

---

### Post by tlstudio on 2010-01-20
Thanks AutoStatic, that's a great idea! I'll give it a try.

---

### Post by tlstudio on 2010-01-20
Well it looks like the problem is solved, I disabled the ondemand service as suggested and the cpus look like they are staying in performance mode now.

Thanks again for all the help guys!

---

### Post by oNNogitaar on 2011-03-31
> **tlstudio said:**
> I downgraded the firmware on the AF12 to 4.8could you tell me how please, the "console" will ony let me upgrade. I have 5.5 now and I tried reinstalling with an older driver but I cannot get the firmware to 4.8...
Thank you!

---

