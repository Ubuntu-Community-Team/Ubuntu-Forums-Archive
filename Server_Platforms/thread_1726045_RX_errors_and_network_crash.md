---
title: "RX errors and network crash"
date: 2011-04-10
forum: Server Platforms
---

### Post by alecm3 on 2011-04-10
I have a server with 2.6.32-30-server 10.04.2 LTS, that has two BroadCom 5709C Ethernet Controllers.

When the network load is medium, everything works fine. When the load becomes higher, I get hundreds of RX errors. 
Under a high network load (large number of connections, high new connection rate), I get

# ifconfig eth0
eth0 Link encap:Ethernet HWaddr e4:1f:13:69:a9:6c 
inet addr:72.172.224.18 Bcast:72.172.224.127 Mask:255.255.255.128
inet6 addr: fe80::e61f:13ff:fe69:a96c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2099602338 **errors:1131715 dropped:1131715 overruns:0 frame:1131715**
TX packets:2113886295 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:136611725547 (136.6 GB) TX bytes:240926946746 (240.9 GB)
Interrupt:28 Memory:92000000-92012800

After this, the network connection crashes, and WAN becomes disconnected.
The bandwidth when this happens is moderate, about 100Mbps. There are about 30000 connections to the server at any time. When I try to reproduce this with iperf, I can do 20 connections with 750Mbps total throughput (i.e. 7.5x higher), and it does not crash the network. 

There is nothing in /var/log/messages or in the BMC controller hardware logs. I replaced the cable and plugged it into a different switch port: the problem is still 100% reproducible.

The port setting match that of on the switch:
# ethtool eth0
Settings for eth0:
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Full 
Advertised pause frame use: No
Advertised auto-negotiation: Yes
Link partner advertised link modes: Not reported
Link partner advertised pause frame use: No
Link partner advertised auto-negotiation: No
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: g
Wake-on: g
Link detected: yes

Has anyone experienced this?

---

### Post by ian dobson on 2011-04-11
Hi,

After abit of digging I've found this:-

This is behavior is only found on Broadcom network cards running on kernel 2.6. Its one of the problem which is not reproducible by a pre defined steps.
By default MSI (Message Signaled Interrupts) is enable on kernel 2.6 and it’s not supported on 2.4 and that causes this intermittent network drop Broadcom cards.

Disabling MSI on Broadcom bnx2 module resolves this problem.

As first attempt, unload the bnx2 driver then 
run modprobe bnx2 disable_msi=1
and test, if that works then:

edit/create modprobe.d/bnx2.conf and add 
options bnx2 disable_msi=1 for permanent setting

Regards
Ian Dobson

---

### Post by alecm3 on 2011-04-11
```
modprobe bnx2 disable_msi=1
```
I will try this, thanks.
is it safe to change this module's parameter remotely on a live server via ssh, or the server needs to be taken off production, and it needs to be done locally from a console?

---

### Post by ian dobson on 2011-04-12
Hi,

It's better to test this during a planned shutdown. I'm not sure about per ssh maybe rmmod bnx2 && modprobe bnx2 disable_msi=1 might work but I wouldn't risk it.

Regards
Ian Dobson

---

### Post by alecm3 on 2011-04-12
> **ian dobson said:**
> Hi,

It's better to test this during a planned shutdown. 
Ian Dobson

I will try this tonight. In the meantime, although I offloaded 50% of the live traffic from this server, there was a load spike, and I saw a small number of errors again:


root@serv10:/# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr e4:1f:13:69:a9:6c  
          inet addr:xx  Bcast:72.172.224.127  Mask:255.255.255.128
          inet6 addr: fe80::e61f:13ff:fe69:a96c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5516353507 **errors:46** **dropped:46** overruns:0 **frame:46**
          TX packets:5547736662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:444339584433 (444.3 GB)  TX bytes:645008121096 (645.0 GB)
          Interrupt:28 Memory:92000000-92012800 

Interestingly, ethtool does not show anything:

root@serv10:/# ethtool -S eth0 | grep error
     rx_error_bytes: 0
     tx_error_bytes: 0
     tx_mac_errors: 0
     tx_carrier_errors: 0
     rx_crc_errors: 0
     rx_align_errors: 0

No errors on the switch port where this is connected, either:

<sw1-48-C03.25>display interface GigabitEthernet1/0/9
 GigabitEthernet1/0/9 current state : UP
 IP Sending Frames' Format is PKTFMT_ETHNT_2, Hardware address is 0016-e0eb-498b
 Media type is twisted pair, loopback not set
 Port hardware type is 1000_BASE_T
 1000Mbps-speed mode, full-duplex mode
 Link speed type is autonegotiation, link duplex type is autonegotiation
 Flow-control is not enabled
 The Maximum Frame Length is 1522
 Broadcast MAX-pps: 3000
 Unknown Multicast Packet drop: Disable
 Unknown Unicast Packet drop: Disable
 Forbid jumbo frame to pass
 PVID: 10
 Mdi type: auto
 Port link-type: access
  Tagged   VLAN ID : none
  Untagged VLAN ID : 10
 Last 300 seconds input:  49389 packets/sec 5145876 bytes/sec
 Last 300 seconds output:  48944 packets/sec 3175866 bytes/sec
 Input(total):  6619597372 packets, - bytes
         - broadcasts, - multicasts, - pauses
 Input(normal):  6619597372 packets, 753728467219 bytes
         350 broadcasts, 9 multicasts, - pauses
 Input:  [B]0 input errors, 0 runts, 0 giants,  - throttles, 0 CRC
         0 frame,  0 overruns, 0 aborts, - ignored, - parity[/B] errors
 Output(total): 6585054577 packets, - bytes
         - broadcasts, - multicasts, - pauses
 Output(normal): 6585054577 packets, 513801708238 bytes
         785295 broadcasts, 6853645 multicasts, 0 pauses
 Output: [B]0 output errors,  - underruns, - buffer failures
         0 aborts, 0 deferred, 0 collisions, 0 late collisions
         - lost carrier, - no carrier[/B]

---

### Post by ian dobson on 2011-04-12
Hi,

Looking at your ethtool results, it looks like it's a driver problem. As the hardware isn't showing any errors, so it must be in the software stack (lost interrupts). What do you see in /proc/interrupts?

Have you tried disable_msi=1?

Regards
Ian Dobson

---

### Post by alecm3 on 2011-04-12
> **ian dobson said:**
> Hi,

Looking at your ethtool results, it looks like it's a driver problem. As the hardware isn't showing any errors, so it must be in the software stack (lost interrupts). What do you see in /proc/interrupts?

Have you tried disable_msi=1?

Regards
Ian Dobson

I will be able to try disable_msi=1 only later today or tomorrow, since the machine needs to be taken off production. I will post the results.

What is the difference between the errors that are reported by ifconfig and ethtool?

root@serv10:/# cat  /proc/interrupts
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       CPU8       CPU9       CPU10      CPU11      CPU12      CPU13      CPU14      CPU15      
   0:       1735          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-edge      timer
   1:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-edge      i8042
   8:          1          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-edge      rtc0
   9:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   acpi
  14:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-edge      ata_piix
  15:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-edge      ata_piix
  16:     249811          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   megasas
  17:     249676          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb5
  18:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb6
  19:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
  21:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   ata_piix
  55:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  56:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  57:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  58:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  59:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  60:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  61:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  62:          3          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      ioat-msix
  63:  458714650          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-0
  64: 1061466726          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-1
  65: 1065280001          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-2
  66: 1036076230          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-3
  67: 1035941213          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-4
  68: 1056664964          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-5
  69: 1033908502          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-6
  70: 1034842874          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-7
  72:   54115969          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-0
  73:   53698724          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-1
  74:   44153799          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-2
  75:   50644952          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-3
  76:   52234846          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-4
  77:   50597471          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-5
  78:   59839873          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-6
  79:   41247505          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1-7
 NMI:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Non-maskable interrupts
 LOC:   49978207   43694202   43359018   43103315   41588665   38769888   37321921   36197874   48728812   42021961   40654378   40781548   34409593   32446931   41075516   30101731   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Performance monitoring interrupts
 PND:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Performance pending work
 RES:   43560517   12951660    9754245    6959920    3005711    2226766    1661668    1072485   24691346    8588057    5982108    4126979    2015364    1291095     900836     665914   Rescheduling interrupts
 CAL:        150        164        174        177     159797        173        165        177        165        180        180        181        166        177        177        175   Function call interrupts
 TLB:    2237492    3100804    2722317    2222561    1020929     935357     809080     614631    1505800    1838217    1485175    1136825     585335     432750     391733     283040   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 MCE:          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711       1711   Machine check polls
 **ERR:         15**
 MIS:          0

I just looked at other servers in this cluster, the ERR value is 0 for the rest of them. This is the only server however with this particular driver:

root@serv10:/# ethtool -i eth0
driver: bnx2
**version: 2.0.2**
firmware-version: 5.2.2 NCSI 2.0.6
bus-info: 0000:0b:00.0

other machines that show ERR 0 have an older driver:
root@serv4:~# ethtool -i eth0
driver: bnx2
version: 1.8.1
firmware-version: 4.6.4 NCSI 1.0.6
bus-info: 0000:0b:00.0

---

### Post by alecm3 on 2011-04-13
```
modprobe bnx2 disable_msi=1
``` did it, I pushed the server to the maximum load, and there are 0 errors shown by ifconfig.

Ian, if you like, PM me here with your address, we will mail you a box of San Francisco local chocolates:wink:!

If it helps anyone in the future, the server was IBM x3550 M3, with 
# ethtool -i eth0
driver: bnx2
version: 2.0.2
firmware-version: 5.2.2 NCSI 2.0.6

# lshw -short
/0/100/1/0           eth0       network    NetXtreme II BCM5709 Gigabit Ethernet
/0/100/1/0.1         eth1       network    NetXtreme II BCM5709 Gigabit Ethernet

A nearly identical IBM x3550 M2 server with
# ethtool -i eth0
driver: bnx2
version: 1.8.1
firmware-version: 4.6.4 NCSI 1.0.6
bus-info: 0000:0b:00.0
never had this problem with MSI enabled. To make sure MSI is really disabled, grep dmesg or /var/log/messages for MSI right after boot, it should not show up there (otherwise you will see serv10 kernel: [327711.246907] bnx2: eth0: using MSIX)

---

