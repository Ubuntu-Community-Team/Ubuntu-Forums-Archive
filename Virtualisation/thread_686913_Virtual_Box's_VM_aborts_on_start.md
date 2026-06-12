---
title: "Virtual Box's VM aborts on start"
date: 2008-02-03
forum: Virtualisation
---

### Post by Pethegreat on 2008-02-03
I have installed Virtual Box and I am trying to run a VM with a .iso file I have on my PC. 

I have the VM set to a drive size of 10gb, 1gb of memory(I have 2gb), 8mb of video memory. 

I try to start the VM and it aborts after 1 second. I looked though the logs, and I found where the problem may be. 

```
00:00:00.968 Debug: HCPhys32BitPD=0000000042e8a000 aHCPhysPaePDs={0000000042eaa000,0000000042eab000,0000000042eac000,0000000042ead000} HCPhysPaePDPTR=0000000042e8b000 HCPhysPaePML4=0000000042e8c000
00:00:00.969 Debug: HCPhysInterPD=000000003d12f000 HCPhysInterPaePDPTR=000000003d132000 HCPhysInterPaePML4=0000000042e89000
00:00:00.969 Debug: apInterPTs={000000003d130000,000000003d131000} apInterPaePTs={0000000042ea4000,0000000042ea5000} apInterPaePDs={0000000042ea6000,0000000042ea7000,0000000042ea8000,0000000042ea9000} pInterPaePDPTR64=0000000042e88000
00:00:00.984 REM: Loading /usr/lib/virtualbox/VBoxREM2.rel at 0x0000000041329010 (30052480 bytes)
00:00:00.984 REM: (gdb) add-symbol-file /usr/lib/virtualbox/VBoxREM2.rel 0x0000000041329010
00:00:01.105 TM: cTSCTicksPerSecond=0x95bc69a8 (2512153000) fTSCVirtualized=true  fTSCUseRealTSC=false fMaybeUseOffsettedHostTSC=false
00:00:01.105 CoreCode: R3=00002aaaaaaab000 R0=ffffc20001efc000 GC=a03a3000 Phys=000000003ae25000 cb=0x1000
00:00:01.173 ERROR [COM]: aRC=0x80004005 aIID={1dea5c4b-0753-4193-b909-22330f64ec45} aComponent={Console} aText={Unable to load R3 module 0.
00:00:01.173 VBox status code: -102 (VERR_FILE_NOT_FOUND)} aPreserve=false
```

From what it looks like I am missing a file. What does code -102 mean?

---

### Post by Jadd on 2008-02-08
I had the same problem. I fixed it by uninstalling virtualbox-ose and virtualbox-ose-source and installing the updated version from [virtualbox.org](virtualbox.org) .

---

