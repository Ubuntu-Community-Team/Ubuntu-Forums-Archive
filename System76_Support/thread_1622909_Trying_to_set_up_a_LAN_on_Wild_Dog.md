---
title: "Trying to set up a LAN on Wild Dog"
date: 2010-11-16
forum: System76 Support
---

### Post by watchpocket on 2010-11-16
I'm trying to set up (on a Wild Dog Performance desktop machine) a home LAN for the first time, so I can use a Roku box.

After first trying with NetworkManager, I'm currently using Wicd. 

[I][COLOR=DarkRed][B]The Roku box sees the network but doesn't connect.
[/B][/COLOR][/I] 
I have no router, and I'm assuming I don't need one. 

Any & all tips welcome.  

Output of several commands follows:

[COLOR=Black]
**sudo lshw -C network**[/COLOR] ```
  *-network               
       description: Ethernet interface
       product: 82567LF-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:27:0e:01:b2:89
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-5 ip=67.81.187.226 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:f100(size=32)
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wmaster0
       version: 01
       serial: 00:24:01:11:e5:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.2 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:e3100000-e310ffff
```**ifconfig**```
eth0      Link encap:Ethernet  HWaddr 00:27:0e:01:b2:89  
          inet addr:67.81.187.226  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::227:eff:fe01:b289/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:155598913 (155.5 MB)  TX bytes:10239299 (10.2 MB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:398 (398.0 B)  TX bytes:398 (398.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:11:e5:e1  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:fe11:e5e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6308 (6.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-11-E5-E1-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```[B]


iwconfig[/B]```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wicd-wifi"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 4E:7E:AE:CC:D1:0B   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[B]


rfkill list[/B]```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```[B]


lspci -nn[/B]```
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce GTS 250] [10de:0615] (rev a2)
02:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)
02:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
```[B]


cat /etc/network/interfaces[/B]```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
     wireless-mode ad-hoc
     wireless-essid wicd-wifi
     address 192.168.0.2
     gateway 192.168.0.1
     netmask 255.255.255.0

#     wireless-key 1234567890
#     wireless-channel 6
```[B]


lsusb[/B]```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0488:00df Cirque Corp. 
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[B]


sudo lshw -short[/B]```
H/W path           Device      Class       Description
======================================================
                               system      Wild Dog Performance
/0                             bus         DP45SG
/0/0                           memory      64KiB BIOS
/0/4                           processor   Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz
/0/4/5                         memory      32KiB L1 cache
/0/4/6                         memory      6MiB L2 cache
/0/2c                          memory      8GiB System Memory
/0/2c/0                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/1                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/2                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/3                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/100                         bridge      4 Series Chipset DRAM Controller
/0/100/1                       bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                     display     G92 [GeForce GTS 250]
/0/100/19          eth0        network     82567LF-2 Gigabit Network Connection
/0/100/1a                      bus         82801JI (ICH10 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801JI (ICH10 Family) USB UHCI Controller #5
/0/100/1a.2                    bus         82801JI (ICH10 Family) USB UHCI Controller #6
/0/100/1a.7                    bus         82801JI (ICH10 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801JI (ICH10 Family) HD Audio Controller
/0/100/1d                      bus         82801JI (ICH10 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801JI (ICH10 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801JI (ICH10 Family) USB UHCI Controller #3
/0/100/1d.7                    bus         82801JI (ICH10 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/0                    bus         FW322/323
/0/100/1e/3        wmaster0    network     AR2413 802.11bg NIC
/0/100/1f                      bridge      82801JIR (ICH10R) LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801JI (ICH10 Family) SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        1TB ST31000528AS
/0/100/1f.2/0/1    /dev/sda1   volume      13GiB EXT3 volume
/0/100/1f.2/0/2    /dev/sda2   volume      7628MiB Linux swap volume
/0/100/1f.2/0/3    /dev/sda3   volume      910GiB EXT3 volume
/0/100/1f.2/1      /dev/scd0   disk        CDDVDW SH-S223C
/0/100/1f.2/0.0.0  /dev/cdrom  disk        CDDVDW SH-S223C
/0/100/1f.3                    bus         82801JI (ICH10 Family) SMBus Controller
```[B]


uanme -a[/B]```
Linux[COLOR=Sienna] [mydomain.com][/COLOR] 2.6.31-22-generic #68-Ubuntu SMP Tue Oct 26 16:37:17 UTC 2010 x86_64 GNU/Linux
```[B]


sudo lsmod[/B]```
Module                  Size  Used by
binfmt_misc            10220  1 
dm_crypt               14888  0 
arc4                    2144  2 
ecb                     3296  2 
ath5k                 137352  0 
mac80211              210040  1 ath5k
led_class               5256  1 ath5k
ath                    10304  1 ath5k
snd_hda_codec_idt      73008  1 
snd_hda_intel          31976  4 
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9384  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
snd                    77192  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
ip_tables              21200  1 iptable_filter
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
x_tables               25832  1 ip_tables
psmouse                58020  0 
serio_raw               6596  0 
cfg80211              109144  3 ath5k,mac80211,ath
joydev                 13088  0 
nvidia              10316904  26 
lp                     11908  0 
parport                40528  1 lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
e1000e                138544  0 
intel_agp              33264  0
```[B]


sudo hwinfo --netcard[/B]```
10: PCI 19.0: 0200 Ethernet controller                          
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_10cd
  Unique ID: rBUF.0N_I7wohxJD
  SysFS ID: /devices/pci0000:00/0000:00:19.0
  SysFS BusID: 0000:00:19.0
  Hardware Class: network
  Model: "Intel 82567LF-2 Gigabit Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x10cd "82567LF-2 Gigabit Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x5001 
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  Memory Range: 0xe3200000-0xe321ffff (rw,non-prefetchable)
  Memory Range: 0xe3224000-0xe3224fff (rw,non-prefetchable)
  I/O Ports: 0xf100-0xf11f (rw)
  IRQ: 26 (527454 events)
  HW Address: 00:27:0e:01:b2:89
  Link detected: yes
  Module Alias: "pci:v00008086d000010CDsv00008086sd00005001bc02sc00i00"
  Driver Info #0:
    Driver Status: e1000e is active
    Driver Activation Cmd: "modprobe e1000e"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 203.0: 0282 WLAN controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_168c_1a
  Unique ID: y9sn.xZ3s5UAJ139
  Parent ID: 6NW+.rH3rArjV8aF
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:03.0
  SysFS BusID: 0000:02:03.0
  Hardware Class: network
  Model: "Atheros AR2413 802.11bg NIC"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x001a "AR2413 802.11bg NIC"
  SubVendor: pci 0x1186 "D-Link System Inc"
  SubDevice: pci 0x3a1d 
  Revision: 0x01
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xe3100000-0xe310ffff (rw,non-prefetchable)
  IRQ: 21 (444895 events)
  HW Address: 00:24:01:11:e5:e1
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000001Asv00001186sd00003A1Dbc02sc00i00"
  Driver Info #0:
    Driver Status: ath5k is active
    Driver Activation Cmd: "modprobe ath5k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (PCI bridge)
```[B]


cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|which|wl'
[/B]```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist twl4030_wdt
# This file lists those modules which we don't want to be loaded by
blacklist eth1394
# Conflicts with dvb driver (which is better for handling this device)
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
```[B]





sudo iwlist scan:[COLOR=black] [COLOR=Blue] (my network is cell 11, ESSID: "wicd-wifi")[/COLOR][/COLOR][/B]```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:DE:A5:96
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"apt_network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023bbd663229
                    Extra: Last beacon: 980ms ago
                    IE: Unknown: 000B6170745F6E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F0300000000000000000000000000000000000000
          Cell 02 - Address: 00:22:3F:D7:53:FC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"avillamar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002281a5839d0
                    Extra: Last beacon: 900ms ago
                    IE: Unknown: 00096176696C6C616D6172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1D:7E:0C:15:65
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"Wende"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=000008d28c036675
                    Extra: Last beacon: 930ms ago
                    IE: Unknown: 000557656E6465
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 00:18:F8:65:6E:F6
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"hottub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fa49f9f9d
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 0006686F74747562
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020004
          Cell 05 - Address: 00:22:75:BA:2E:8F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Odyssey E1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002932a4400b
                    Extra: Last beacon: 370ms ago
                    IE: Unknown: 000A4F647973736579204531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F0000000000000000000000000000000000000000
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B0001031047001000000000000000011000002275BA2E8F1021001242656C6B696E20436F72706F726174696F6E1023000C463644343233302D3420763310240007332E30302E30331042000E31323933323432333035313433331054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD050050F20500
          Cell 06 - Address: 00:23:69:AD:03:6E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Penelope"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000580d473183
                    Extra: Last beacon: 480ms ago
                    IE: Unknown: 000850656E656C6F7065
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A344D333439371054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:25:9C:1E:98:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"rm929"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006962a34a3e
                    Extra: Last beacon: 390ms ago
                    IE: Unknown: 0005726D393239
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
          Cell 08 - Address: 00:23:F8:4C:B0:9A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"LK420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000046b267086
                    Extra: Last beacon: 230ms ago
                    IE: Unknown: 00054C4B343230
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010024FF7F
          Cell 09 - Address: 00:1F:90:B7:7F:9C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"2XPS5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000081ec5a1c5
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 00053258505335
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 10 - Address: 00:25:9C:D9:DA:A5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"mcs23nov"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000384b7b148b
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00086D637332336E6F76
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700103719AB0854F5BB8B0B5134FB690A20FE102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180201F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          [COLOR=Red]Cell 11 - Address: 4E:7E:AE:CC:D1:0B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                   [/COLOR][COLOR=Red] ESSID:"wicd-wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 8544010ms ago
                    IE: Unknown: 0009776963642D77696669
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C[/COLOR]
          Cell 12 - Address: 00:18:39:EB:58:DF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"ps3-2010"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038e25b37557
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00087073332D32303130
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 13 - Address: 00:25:9C:39:3C:6E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Kish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009a97de93ff
                    Extra: Last beacon: 50ms ago
                    IE: Unknown: 00044B697368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700106AFB34594A025A1C3D89D46E347ABD0D102100074C696E6B737973102300075752543331304E102400063132333435361042000234321054000800060050F2040001101100075752543331304E100800020084
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 14 - Address: 00:1F:F3:04:B6:29
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"APX Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000055faf56f082
                    Extra: Last beacon: 230ms ago
                    IE: Unknown: 000B415058204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B12
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0020
          Cell 15 - Address: 00:1F:90:F2:3F:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"LBQ43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a219f8602
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00054C42513433
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
```
([COLOR=Red]The output of the following command was edited[/COLOR], because there were a few dozen instances of the line: "[COLOR=Indigo]wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)[/COLOR]" re-appearing over  & over.)

**dmesg | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|usb|witch|wl'**```
[    0.000000] No NUMA configuration found
[    0.000000] found SMP MP-table at [ffff8800000fd4e0] fd4e0
[    0.000000] No AGP bridge found
[    0.632907] ACPI: No dock devices found.
[    0.638140] usbcore: registered new interface driver usbfs
[    0.638140] usbcore: registered new interface driver hub
[    0.638140] usbcore: registered new device driver usb
[    0.690004] Switched to high resolution mode on CPU 0
[    0.691421] Switched to high resolution mode on CPU 1
[    0.691433] Switched to high resolution mode on CPU 3
[    0.691489] Switched to high resolution mode on CPU 2
[    0.711427] pnp: PnP ACPI: found 11 devices
[    4.990061] usb usb1: configuration #1 chosen from 1 choice
[    4.990079] hub 1-0:1.0: USB hub found
[    5.010042] usb usb2: configuration #1 chosen from 1 choice
[    5.010058] hub 2-0:1.0: USB hub found
[    5.010283] usb usb3: configuration #1 chosen from 1 choice
[    5.010301] hub 3-0:1.0: USB hub found
[    5.010456] usb usb4: configuration #1 chosen from 1 choice
[    5.010474] hub 4-0:1.0: USB hub found
[    5.010625] usb usb5: configuration #1 chosen from 1 choice
[    5.010641] hub 5-0:1.0: USB hub found
[    5.010789] usb usb6: configuration #1 chosen from 1 choice
[    5.010805] hub 6-0:1.0: USB hub found
[    5.010962] usb usb7: configuration #1 chosen from 1 choice
[    5.010977] hub 7-0:1.0: USB hub found
[    5.011123] usb usb8: configuration #1 chosen from 1 choice
[    5.011140] hub 8-0:1.0: USB hub found
[    5.011208] PNP: No PS/2 controller found. Probing ports directly.
[    5.015696] device-mapper: multipath: version 1.1.0 loaded
[    5.015700] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.017190] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.593755] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.780330] usb 3-1: configuration #1 chosen from 1 choice
[    6.060005] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    6.169669] usbcore: registered new interface driver hiddev
[    6.183492] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
[    6.183544] generic-usb 0003:046D:C040.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    6.183556] usbcore: registered new interface driver usbhid
[    6.183558] usbhid: v2.6:USB HID core driver
[    6.246358] usb 3-2: configuration #1 chosen from 1 choice
[    6.290721] input: Cirque GlidePoint as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    6.290779] generic-usb 0003:0488:00DF.0002: input,hidraw1: USB HID v1.10 Keyboard [Cirque GlidePoint] on usb-0000:00:1a.0-2/input0
[    6.312399] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:27:0e:01:b2:89
[    6.312401] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    6.312426] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[   19.506838] lp: driver loaded but no devices found
[   19.714408] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.945193] ath5k 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.945228] ath5k 0000:02:03.0: registered as 'phy0'
[   20.473724] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   20.473780] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.473817] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.473856] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.473891] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10



[   20.473929] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.473966] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   20.530292] ath: EEPROM regdomain: 0x10
[   20.530294] ath: EEPROM indicates we should expect a direct regpair map
[   20.530296] ath: Country alpha2 being used: CO
[   20.530297] ath: Regpair used: 0x10
[   20.535122] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   20.641943] wlan0: Trigger new scan to find an IBSS to join
[   20.753350] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   20.832685] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   20.910702] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   20.992070] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.073787] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.160571] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.249302] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.303078] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   21.303081] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.303737] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.328666] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.412995] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   21.495672] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   23.953759] wlan0: Trigger new scan to find an IBSS to join
[   26.953761] wlan0: Trigger new scan to find an IBSS to join
[   27.074065] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.162344] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.242791] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.334282] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.422921] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.510184] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.586596] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.668948] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.755533] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.845026] ath5k phy0: bf=ffff8802001ead00 bf_skb=(null)
[   27.936588] wlan0: Creating new IBSS network, BSSID 4e:7e:ae:cc:d1:0b
[   31.041652] wlan0: no IPv6 routers present
[   31.450004] eth0: no IPv6 routers present
[   57.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  105.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  137.040024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  884.534795] ath5k phy0: unsupported jumbo
```

---

### Post by isantop on 2010-11-16
Actually, I'd go with a router. 

Basically, in order for that to work properly, you'd have to set up your Wild Dog to act as a router. It can be done, but it is simpler to just use the router. You really can't beat the "plug it in and go" convenience a router offers.

---

### Post by watchpocket on 2010-11-16
Thanks for the info.  Router recommendations, anyone?

What plays nicest with Ubuntu Karmic/Lucid/Maverick ??

---

### Post by isantop on 2010-11-17
Thankfully, routers are near universal since they usually talk to each other/computers via the internet protocol. WiFi is also standardized, though there are manufacturers that put additions to the standards that may not be compatible. These can usually be disabled (I'm looking at you, WPS!)

If you'd like a specific recommendation, we use a D-Link DIR-625 here in the office, and it works wonderfully.

---

### Post by watchpocket on 2010-11-18
Thanks, I'll get a router.

---

