---
title: "GPU passthrough quality of life improvements"
date: 2016-12-10
forum: Virtualisation
---

### Post by wbrb on 2016-12-10
Ubuntu 16.04.1 Server KVM
```
Linux vm03 4.4.0-34-generic #53 SMP Sun Aug 21 22:05:05 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux
```
guest running 16.04.1 Desktop VM
```
Linux u1604dt05 4.7.0-040700rc6-generic #201607040332 SMP Mon Jul 4 07:34:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

I've been running a 2 (independent) GPUs with one of the passedthrough to a guest for a while now and this runs nicely but I'm having some issues and I'm having trouble capturing them in the logs figuring them out.

**Issue #1**
I have the ACS patch applied to my kernel but it seems to keep reverting each reboot and bunching up my iommu groups. To fix this I have to re dpkg -i the patched kernel and reboot. Basically on boot I check my iommu groups:
```
find /sys/kernel/iommu_groups/ -type l
```
And every time I boot they're wrong until I reinstall the kernel and reboot. How do I make the patched version permanent?

**Issue #2**
When I passthrough keyboard and mouse from hypervisor I have to unplug and plug them in. syslog on the hypervisor seems to indicated this is an apparmor issue? I thought I had read this was something about the usb devices being initialized prior to kvm starting.
```
Dec 10 14:26:34 vm03 kernel: [  135.400479] audit: type=1400 audit(1481397994.380:23): apparmor="DENIED" operation="open" profile="libvirt-2f647e4b-aff2-4228-bbcd-f0484fe2bf77" name="/run/udev/data/c189:1" pid=1631 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=111 ouid=0
```
Again after unplug/replug:
```
Dec 10 14:26:53 vm03 kernel: [  154.476791] audit: type=1400 audit(1481398013.457:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-2f647e4b-aff2-4228-bbcd-f0484fe2bf77//qemu_bridge_helper" pid=1827 comm="apparmor_parser"
```

My attach script if it matters:
```
#!/bin/bash

#mouse

MVID=$(lsusb | sed 's/:/ /g' | gawk '/075c/ {print $6}')
MPID=$(lsusb | sed 's/:/ /g' | gawk '/075c/ {print $7}')

echo "mouse using $MVID $MPID"

sed 's/VID/'"$MVID"'/;s/PID/'"$MPID"'/' ./dev.xml > m.xml

virsh detach-device u1604dt05 /root/m.xml
virsh attach-device u1604dt05 /root/m.xml

#kb

KVID=$(lsusb | sed 's/:/ /g' | gawk '/c31c/ {print $6}')
KPID=$(lsusb | sed 's/:/ /g' | gawk '/c31c/ {print $7}')

echo "keyboard using $KVID $KPID"

sed 's/VID/'"$KVID"'/;s/PID/'"$KPID"'/' ./dev.xml > kb.xml

virsh detach-device u1604dt05 /root/kb.xml
virsh attach-device u1604dt05 /root/kb.xml

#Bus 003 Device 007: ID 045e:075c Microsoft Corp. 
#Bus 003 Device 006: ID 046d:c31c Logitech, Inc. Keyboard K120
```
How to I permit this to work the first time?

**Issue #3**
My GPU occasionally (twice a week?) crashes, I can restart the vm once. If it crashes again I am unable to restart the vm a second time. I'm unable to determine the cause from the logs on both the guest and the host.

Per:
```
lspci -vvvs 2:00.0
lspci -vvvs 2:00.1
```

Normally my GPU looks like this (from KVM):
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev cf) (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited / Sapphire Technology Device e344
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 33
	Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=2M]
	Region 4: I/O ports at d000 [size=256]
	Region 5: Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at d0240000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 8GT/s, Width x8, ASPM L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR+, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
		LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
			 EqualizationPhase2+, EqualizationPhase3+, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee003d8  Data: 0000
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v2] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [200 v1] #15
	Capabilities: [270 v1] #19
	Capabilities: [2b0 v1] Address Translation Service (ATS)
		ATSCap:	Invalidate Queue Depth: 00
		ATSCtl:	Enable-, Smallest Translation Unit: 00
	Capabilities: [2c0 v1] #13
	Capabilities: [2d0 v1] #1b
	Capabilities: [320 v1] Latency Tolerance Reporting
		Max snoop latency: 0ns
		Max no snoop latency: 0ns
	Capabilities: [328 v1] Alternative Routing-ID Interpretation (ARI)
		ARICap:	MFVC- ACS-, Next Function: 1
		ARICtl:	MFVC- ACS-, Function Group: 0
	Capabilities: [370 v1] L1 PM Substates
		L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
			  PortCommonModeRestoreTime=0us PortTPowerOnTime=170us
	Kernel driver in use: vfio-pci

02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
	Subsystem: PC Partner Limited / Sapphire Technology Device aae0
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at d0260000 (64-bit, non-prefetchable) [disabled] [size=16K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 8GT/s, Width x8, ASPM L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR+, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v2] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [328 v1] Alternative Routing-ID Interpretation (ARI)
		ARICap:	MFVC- ACS-, Next Function: 0
		ARICtl:	MFVC- ACS-, Function Group: 0
	Kernel driver in use: vfio-pci
	Kernel modules: snd_hda_intel

```

And like this from the guest:
```
lspci -vvvs 00:02.0
00:02.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev cf) (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited / Sapphire Technology Device e344
	Physical Slot: 2
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=2M]
	Region 4: I/O ports at c000 [size=256]
	Region 5: Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 8GT/s, Width x8, ASPM L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR+, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
			 EqualizationPhase2+, EqualizationPhase3+, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee03000  Data: 4022
	Kernel driver in use: amdgpu
	Kernel modules: amdgpu

```

After the second crash it looks like this:
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: vfio-pci

02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0 (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: vfio-pci
	Kernel modules: snd_hda_intel

```

I have no idea what it looks like from the guest because the machine has hung. In the logs I see this a few times:
```
Dec 10 14:21:36 vm03 kernel: [141155.373612] vfio-pci 0000:02:00.0: Refused to change power state, currently in D3
```

This a couple dozen times:
```
Dec 10 14:21:37 vm03 kernel: [141156.223634] vfio_ecap_init: 0000:02:00.0 hiding ecap 0xffff@0xffc

```
This a couple hundred times:
```
Dec 10 14:21:36 vm03 kernel: [141155.373612] vfio-pci 0000:02:00.0: Refused to change power state, currently in D3
```

and then after the crash, this every time I try (and fail) to restart the guest vm:
```
Dec 10 14:21:38 vm03 kernel: [141156.957651] vfio-pci 0000:02:00.0: timed out waiting for pending transaction; performing function level reset anyway
```

However I have no idea how to capture info about the actual crash event. All the logs seem to show nothing at that moment. It seems to occur around these usb messages but I have no idea if they're related:
```
Dec 10 14:20:11 vm03 kernel: [141070.630621] usb 3-14: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Dec 10 14:20:11 vm03 kernel: [141070.630624] usb 3-14: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
```

Any observations / suggestions / feedback welcome. None of the above are really a show stoppers but it's *nix and not win so rebooting the hypervisor every couple days feels wrong. :P

---

### Post by kvasko on 2016-12-15
I had same issue. When your gpu goes into the "02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev ff) (prog-if ff)" state, it indicated that the device isn't coming back from a bus reset properly. I would update your kernel on host to the latest version, but in my case it was a hardware issue.

It happens when your VM shuts down, the bus resets the card, the card/bus doesn't come back properly from the bus reset. There is code in those threads I linked below that will allow you to test it outside of a VM. 

See these threads.

[https://www.redhat.com/archives/vfio-users/2016-October/msg00078.html](https://www.redhat.com/archives/vfio-users/2016-October/msg00078.html)
[https://www.redhat.com/archives/vfio-users/2016-October/msg00083.html](https://www.redhat.com/archives/vfio-users/2016-October/msg00083.html)

I've fought with GPU Passthrough for the last 6 months and it is not very stable unfortunately.

---

### Post by wbrb on 2016-12-18
I've spent the last couple days looking into this.

Your back and forth with Alex was very informative about some of the inner workings of PCIE w/ KVM. I was concerned this was due to the AMD RX 4xx / Polaris being newer so to see the same bus issue with team green as well as team red is reassuring. I always like to be reminded of how much I still have to learn.

Your troubleshooting got pretty intense at:
```
setpci -s 3:00.0 82.w=8:8
```
I've never had a need to directly manipulate a PCI device before. :)

Did you end up reaching out to NVIDIA for information about the behavior of the PLX switches on the Titan X? After reading [this I think I get how PLX PEX works]("http://www.anandtech.com/show/6170/four-multigpu-z77-boards-from-280350-plx-pex-8747-featuring-gigabyte-asrock-ecs-and-evga?_ga=1.199047791.1370071003.1481834220") and am now slightly concerned about my motherboard.

I went back and started reading the PCIE specs for my motherboard more closely, it's an ASRock Z87 Extreme4. It has 2 x16 slots but multiple independent video operation is not a "supported" configuration, SLI/Crossfire with both @ x8 is. (I have no idea if "supported" matters). I wanted to try passing the RX460 in from slot PCEI2 (x16) instead of slot PCIE4 (x8) even though the RX460 is only x8 just to see if there's some motherboard HW issue I've missed. But now vga arbiter is grabbing my RX460 on boot instead of my HD5450 and I'm getting errors. [ASRock Z87 Extreme4]("http://www.asrock.com/mb/Intel/Z87%20Extreme4/index.us.asp?cat=Specifications")

```
vfio-pci 0000:01:00.0: BAR 0: can't reserve [mem 0xe0000000-0xefffffff 64bit pref]
```
```
vfio-pci 0000:01:00.0: Invalid ROM contents
```

Everything I read shows that default VGA adapter is supposed to be a BIOS setting but my BIOS lacks this. I'm playing yanking the secondary card and using fbcon=map:0 to see if I can just go headless for testing. 

All this got me thinking about my 8 FPS in XCOM2 @ 1080. I assumed it was a poor performance linux port / unsupported video / something else but I realized it looks like the CPU is bottlenecking the GPU. So I yanked my disk with KVM and dumped a disk for a standard single card installation of Ubuntu Desktop 16.04.1 (4.8) w/ mesa 13.x and now see what "normal" performance looks like. I'll try KVM once 16.04.2 LTS releases to see if the issue was 4.4 kernel hypervisor w/ACS running 4.7 kernel desktop guest or I will upgrade to an X99 2011-3 motherboard w/ Haswell-EP and real ACS that doesn't have these issues. 

I've setup the 16.04.1 Desktop machine now and the performance is much better. My continuing issues will mesa 13 crashes will be posted in hardware or gaming. Thanks.

---

