---
title: "opvxa1200 can't work with DAHDI 2.2.1 on UBUNTU Server 10.04 &quot;Lucid Lynx&quot;"
date: 2010-05-24
forum: Server Platforms
---

### Post by zhangr on 2010-05-24
I've installed ubuntu server 10.04 "Lucid Lynx" on our product server.

We need Asterisk to handle telephone calls in our environment.

I'm happy when I found the analog card driver we bought has been included in the "DAHDI" package of this distribution. Then I migrate the hard ware into this server which has "Lucid" been installed. After install the hardware, I found the driver can't work with the hardware.

Description:
The analog card we bought is OpenVox a1200p, click [here]("http://www.openvox.cn/products/show.php?itemid=42&lang=2") for more details.
After installed asterisk dahdi and the dependency (solved by apt). I can load the module "opvxa1200"(modprobe opvxa1200), but when I tried to scan the device (dahdi_scan), the server can only find an virtual device, seems like this:
```
[1]
active=yes
alarms=UNCONFIGURED
description=DAHDI_DUMMY/1 (source: HRtimer) 1
name=DAHDI_DUMMY/1
manufacturer=
devicetype=DAHDI Dummy Timing
location=
basechan=1
totchans=0
irq=0
```On a working box, this command should show something like this:
```
[1]
active=yes
alarms=OK
description=OpenVox A1200P/A800P Board 13
name=OPVXA1200/12
manufacturer=OpenVox
devicetype=OpenVox A1200P/A800P
location=PCI Bus 01 Slot 04
basechan=1
totchans=12
irq=193
type=analog
port=1,FXO
port=2,FXO
port=3,none
port=4,none
port=5,none
port=6,none
port=7,none
port=8,none
port=9,none
port=10,none
port=11,none
port=12,none
```I've tried to compile the driver myself, and I found I must include an header file "linux/sched.h" which comes from kernel-headers package. I download the dahdi driver from [asterisk.org]("http://www.asterisk.org/"), you can find a full version list [here]("http://downloads.asterisk.org/pub/telephony/dahdi-linux-complete/releases/").
Dahdi version 2.2.0 which works well on our old server can not work with the kernel which "Lucid" have. Because lack of "#include linux/sched.h" in all driver source code.

Dahdi version 2.2.1 works with the kernel "Lucid" have, And I follow the reference comes from OpenVox: [wiki]("http://wiki.openvox.cn/index.php/OpenVox_A1200P_Dahdi_en")

The driver I've generated still doesn't work with the kernel 2.6.32 "Lucid" have.
Seems Ubuntu Foundation "just" compile the driver but never tested it, does any one have a solution?

---

### Post by zhangr on 2010-05-24
okay, I went to contact the manufacturer, they told opvxa1200 conflicts with some modules which kernel decide to load automatically, after you installed the hardware, try to say "lspci -v", you'll get something like this:
```

09:0d.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
        Subsystem: Device 8519:0003
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at 1000 
        Memory at f8c10000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: netjet
        Kernel modules: wcopenpci, opvxa1200, hisax, netjet

```Module opvxa1200 conflicts with hisax and netjet, so we've to blacklist them in /etc/modprobe.d/blacklist.conf, add following code:
```

# disable kernel load modules which conflicts with opvxa1200 analog card driver
blacklist hisax
blacklist netjet

```then unload the module in memory:
```

sudo rmmod hisax
sudo rmmod netjet

```restart dahdi:
```

sudo /etc/init.d/dahdi restart

```then run "dahdi_scan" to check whether the driver works:
```

[1]
active=yes
alarms=UNCONFIGURED
description=DAHDI_DUMMY/1 (source: HRtimer) 1
name=DAHDI_DUMMY/1
manufacturer=
devicetype=DAHDI Dummy Timing
location=
basechan=1
totchans=0
irq=0
type=analog
[2]
active=yes
alarms=OK
description=OpenVox A1200P/A800P Board 13
name=OPVXA1200/12
manufacturer=OpenVox
devicetype=OpenVox A1200P/A800P
location=PCI Bus 09 Slot 14
basechan=1
totchans=12
irq=16
type=analog
port=1,FXO
port=2,FXO
port=3,none
port=4,none
port=5,none
port=6,none
port=7,none
port=8,none
port=9,none
port=10,none
port=11,none
port=12,none

```Special thanks following people helping me solving the problem:
[EMAIL="xin.liu@openvox.cn"]xin.liu@openvox.cn[/EMAIL]
[EMAIL="james.zhu@openvox.cn"]james.zhu@openvox.cn[/EMAIL]

---

