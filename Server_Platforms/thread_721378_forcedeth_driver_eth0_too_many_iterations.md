---
title: "forcedeth driver: eth0: too many iterations"
date: 2008-03-11
forum: Server Platforms
---

### Post by upnix on 2008-03-11
Running Ubuntu 7.10, with all the updates. My current kernel is 2.6.22-14-server.

I'm getting this error, which is (fairly sure) killing an NFS connection that is rather important:

[38050.090000] eth0: too many iterations (21) in nv_nic_irq.
[38193.060000] eth0: too many iterations (21) in nv_nic_irq.

etc.

I get this error while reading and writing to NFS, as quickly as my 1 gig connection will allow.

I see a lot of mentions of setting max_interrupt_work. So, I started at 10 and worked up to 20, but the problem persists. I've also seen talk of "MSI" and "MSIX" which I'm not clear on. I've tried with both set to '1' and both set to '0', which made no difference.

Further information on hardware below; any help would be appreciated.

Chris

ccameron@nfs01:~$ dmesg | grep eth
[ 2.640000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[ 6.340000] forcedeth: using HIGHDMA
[ 6.360000] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:08.0
[ 6.360000] forcedeth: using HIGHDMA
[ 6.910000] eth1: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:09.0
[ 20.540000] eth0: no IPv6 routers present

lspci -vvv output:
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
Subsystem: nVidia Corporation Unknown device cb84
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0 (250ns min, 5000ns max)
Interrupt: pin A routed to IRQ 17
Region 0: Memory at fe9f6000 (32-bit, non-prefetchable) [size=4K]
Region 1: I/O ports at a400 [size=8]
Region 2: Memory at fe9fa800 (32-bit, non-prefetchable) [size=256]
Region 3: Memory at fe9fa400 (32-bit, non-prefetchable) [size=16]
Capabilities: [44] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
Vector table: BAR=2 offset=00000000
PBA: BAR=3 offset=00000000
Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
Address: 0000000000000000 Data: 0000
Masking: 00000000 Pending: 00000000
Capabilities: [6c] HyperTransport: MSI Mapping

---

