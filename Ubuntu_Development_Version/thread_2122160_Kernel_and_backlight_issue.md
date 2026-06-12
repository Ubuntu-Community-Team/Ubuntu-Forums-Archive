---
title: "Kernel and backlight issue"
date: 2013-03-04
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-04
i attached a recording at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168/+attachment/3577086/+files/backlight-bug-linux-3.7_3.8_3.9.mp4](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168/+attachment/3577086/+files/backlight-bug-linux-3.7_3.8_3.9.mp4)

this only started happening after a bios upgrade, i went from 207 to 210 and there are 2 notes "Support 2013 Power Saving" and "Update ME Firmware"
**requires monitor with back-light controls, like a notebook/laptop/netbook
```
~$ uname -r;xbacklight -set 0;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;
3.8.2-030802-generic
100.000000
90.000000
91.000000
90.000000
91.000000
90.000000

```
```
~$ uname -r;xbacklight -set 0;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;
3.8.0-9-generic
100.000000
90.000000
91.000000
90.000000
91.000000
90.000000

``````
~$ uname -r;xbacklight -set 0;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;
3.6.11-030611-generic
0.000000
0.000000
0.000000
0.000000
0.000000
0.000000
```
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168)
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 13c7
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 49
    Region 0: Memory at dd000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee00000  Data: 4052
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [a4] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: i915
    Kernel modules: i915
```

---

### Post by ventrical on 2013-03-04
3.8.0-9-generic
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:
sudo apt-get install xbacklight
The program 'xbacklight' is currently not installed. You can install it by typing:

installed it:

 now:
 uname -r;xbacklight -set 0;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;xbacklight -get;
3.8.0-9-generic
ventrical@ventrical-P4M266A-8237:~$

---

### Post by pqwoerituytrueiwoq on 2013-03-04
i assume you are using a desktop, so there is no backlight for xbacklight to control

---

### Post by ventrical on 2013-03-04
Doh. !  I'll pull out the Acer. :) lol

sorry bout that!

---

### Post by pqwoerituytrueiwoq on 2013-03-15
[**[COLOR=#DD4814][B]ventrical**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1140838") how did that turn out?
also i added a recording to launchpad of the issue

---

