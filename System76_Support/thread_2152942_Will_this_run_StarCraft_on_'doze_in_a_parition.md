---
title: "Will this run StarCraft on 'doze in a parition?"
date: 2013-06-09
forum: System76 Support
---

### Post by jcllings on 2013-06-09
I'm assessing a situation that has been a pain in my 6 for quite some time.  The fact that Blizzard won't release StarCraft for Linux and that it doesn't run worth crud under a VM or Wine. 
What I wan't is a small 'doze partition dedicated to SC. I have a proper & legal Windows license for this purpose. The hardware is what I am looking at. Specifically the graphics since this machine beats my old heat sensitive 'doze laptop all hollow in other categories. 

System76 Model: panp9 (one of the first IvyBridge's)

Reccomended graphics hardware from the Blizzard web site:
NVIDIA® GeForce® 8800 GT (512 MB) or ATI™ Radeon™ HD 4850 or better

Absolute minium graphics hardware from the Blizzard web site:
NVIDIA® GeForce® 7600 GT or ATI™ Radeon™ X800 XT or better

I've collected logs.tar and attached it. Below is some parsing of those files but I don't recognize much that I am seeing here. What I need is the name of the graphics card so that I can compare before I go and re-partition everything. 

XXX@XXXXXXXX:~/temp/tmp/system_logs_20130608_h11m19s57$ rgrep VGA * 
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
lspci:    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
lspci:    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Xorg.0.log:[    12.500] (II) intel(0): Output VGA1 has no monitor section
Xorg.0.log:[    12.664] (II) intel(0): EDID for output VGA1
Xorg.0.log:[    12.828] (II) intel(0): Output VGA1 disconnected
jim@blacklightning:~/temp/tmp/system_logs_20130608_h11m19s57$ rgrep graphics * 
jim@blacklightning:~/temp/tmp/system_logs_20130608_h11m19s57$ rgrep raphics * 
dmesg:[    4.144490] [drm] MTRR allocation failed.  Graphics performance may suffer.
lspci:00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
syslog:Jun  8 11:08:12 blacklightning kernel: [    3.973262] [drm] MTRR allocation failed.  Graphics performance may suffer.
syslog:Jun  8 11:19:14 blacklightning kernel: [    4.144490] [drm] MTRR allocation failed.  Graphics performance may suffer.
Xorg.0.log:[    12.466] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
Xorg.0.log:[    12.468] (II) intel(0): Integrated Graphics Chipset: Intel(R) 
XXX@XXXXXXXX:~/temp/tmp/system_logs_20130608_h11m19s57$

---

### Post by Cheesemill on 2013-06-09
You have an integrated Intel graphics chip built into the CPU.

You ***should*** be able to get playable frame rates in SCII using it although only on low settings.

I can give you more information if you can tell us exactly which processor your machine has. If you are unsure you can find out with the following command...
```
cat /proc/cpuinfo | grep model
```

---

### Post by jcllings on 2013-06-09
> **Cheesemill said:**
> You have an integrated Intel graphics chip built into the CPU.
You ***should*** be able to get playable frame rates in SCII using it although only on low settings.
I can give you more information if you can tell us exactly which processor your machine has. If you are unsure you can find out with the following command...
```
cat /proc/cpuinfo | grep model
```

Drive is an Intel 520 series SSD and here is the CPU info. Some brand of IvyBridge according to what they told me. Got a free CPU upgrade because they didn't have the one I wanted. Dag zippy on Linux which is why I was more concerned with the graphics: 

xxx@xxxxxxxxxx:~$ cat /proc/cpuinfo | grep model
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
model           : 58
model name      : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz

---

### Post by Cheesemill on 2013-06-09
CPU power shouldn't be an issue, but knowing the CPU model lets us know exactly which graphics chip you have as the graphics chip is built in to the processor.

That CPU has integrated Intel HD4000 graphics, you'll get around 30FPS at 1360x768 on medium settings with StarCraft II.

[http://www.notebookcheck.net/Intel-HD-Graphics-4000-Benchmarked.73567.0.html](http://www.notebookcheck.net/Intel-HD-Graphics-4000-Benchmarked.73567.0.html)

---

