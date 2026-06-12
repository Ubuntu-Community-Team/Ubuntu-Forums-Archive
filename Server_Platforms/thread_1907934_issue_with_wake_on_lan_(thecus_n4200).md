---
title: "issue with wake on lan (thecus n4200)"
date: 2012-01-12
forum: Server Platforms
---

### Post by cramren on 2012-01-12
Hello all,

this is my first post so please bear with me.

A while ago I bought a Thecus n4200 NAS, because it is a nice compact machine and Wake on LAN is advertised. I have replaced the IDE flash module with a 8 GB version. The OS, currently Ubuntu 12.04, is installed on this module. Everything runs smoothly except Wake on LAN. I have tried almost all solutions which I could find on the net. But the result was all the same. Susupend, hibernate and suspend-hybrid are functioning.

I have two issues, which I would like to address to the forum:

1. After a suspend-hibrid has succeeded, the machine wakes up after about 10 minutes and goes to sleep again immediatly.

2. When I send a magic packet to the suspended machine it does not wake up. Waking it up by pressing the power button works.

I have tried this under 10.04, 11.10 and 12.04 all with the same result. Maybe someone has an enlightening idea. I would very much appreciate it.

Regards.

Here's the information how the system is configured:

- BIOS option "Wake on PCI" is set.
- The parameter "NETDOWN" in "/etc/init.d/halt" is set to "no"

```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo -n PEX0 | tee /proc/acpi/wakeup
exit 0

``````
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address x.x.x.x
    netmask 255.255.255.0
    gateway x.x.x.x
    ethernet_wol g

``````
$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: off
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000001 (1)
                   drv
    Link detected: yes

``````
$ lspci -tv
-[0000:00]-+-00.0  Intel Corporation N10 Family DMI Bridge
           +-1a.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4
           +-1a.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5
           +-1a.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6
           +-1a.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2
           +-1b.0  Intel Corporation 82801I (ICH9 Family) HD Audio Controller
           +-1c.0-[01]----00.0  Intel Corporation 82574L Gigabit Network Connection
           +-1c.1-[02]----00.0  Intel Corporation 82574L Gigabit Network Connection
           +-1c.3-[03]--+-00.0  ATI Technologies Inc RV710 [Radeon HD 4350]
           |            \-00.1  ATI Technologies Inc RV710/730 HDMI Audio [Radeon HD 4000 series]
           +-1c.4-[04]--+-00.0  JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
           |            \-00.1  JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
           +-1d.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1
           +-1e.0-[05]--
           +-1f.0  Intel Corporation 82801IR (ICH9R) LPC Interface Controller
           +-1f.2  Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode]
           \-1f.3  Intel Corporation 82801I (ICH9 Family) SMBus Controller

``````
$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
PCI0      S5    *disabled  no-bus:pci0000:00
PEX0      S5    *enabled   pci:0000:00:1c.0
PEX1      S5    *disabled  pci:0000:00:1c.1
PEX2      S5    *disabled  
PEX3      S5    *disabled  pci:0000:00:1c.3
PEX4      S5    *disabled  pci:0000:00:1c.4
PEX5      S5    *disabled  
HUB0      S5    *disabled  pci:0000:00:1e.0
UAR1      S5    *disabled  pnp:00:07
UAR2      S5    *disabled  pnp:00:08
IGBE      S5    *disabled  
USB0      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *enabled   pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USB3      S3    *enabled   pci:0000:00:1a.0
USB4      S3    *enabled   pci:0000:00:1a.1
USB5      S3    *enabled   pci:0000:00:1a.2
EHC1      S3    *enabled   pci:0000:00:1d.7
EHC2      S3    *enabled   pci:0000:00:1a.7
AZAL      S5    *disabled  pci:0000:00:1b.0

```

---

### Post by rubylaser on 2012-01-12
I don't have a Thecus, but all I've ever done in the past to enable wake on LAN is to enable it in the BIOS as you've done. Next, install ethtool, and make sure your device supports WOL, which is does. Run this command to make sure it's currently running...
```
ethtool -s eth0 wol g
```

Finally, I add a line like this to /etc/network/interfaces.
```
auto eth0
iface eth0 inet static 
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
up ethtool -s eth0 wol g
```

That is literally all I ever do, and as long as the device supports WOL, I've never had a problem getting this working. 

Or, you can do it like this.
```

auto eth0
iface eth0 inet static 
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
ethernet-wol g

```
**With a dash, not an underscore as you have above.**

---

### Post by cramren on 2012-01-13
Thank you very much for your reply.

I will try your suggestion replacing the underscore with a dash in the file "/etc/network/interfaces" over the weekend.

---

### Post by cramren on 2012-01-18
Sadly, no change. The machine simply does not wake up.

Isn't there anyone with a thecus and a working wol?

---

### Post by rubylaser on 2012-01-18
I don't have one, so I can't help you out there, other than to say if the device supports it, and it's turned on in the BIOS, these directions should work.

---

