---
title: "Wireless and Bluetooth on Atheros AR9565"
date: 2018-06-14
forum: Ubuntu/Debian BASED
---

### Post by msmaldi on 2018-06-14
My wireless connection sometime stop work, if I turn off bluetooth, network automatic work perfect.


dmesg

```
[   17.884402] ath: phy0: WB335 2-ANT card detected[   17.884405] ath: phy0: Set BT/WLAN RX diversity capability
[   17.891774] ath: phy0: Enable LNA combining
[   17.895691] ath: phy0: ASPM enabled: 0x42
[   17.895694] ath: EEPROM regdomain: 0x65
[   17.895695] ath: EEPROM indicates we should expect a direct regpair map
[   17.895698] ath: Country alpha2 being used: 00
[   17.895699] ath: Regpair used: 0x65
[   17.910827] intel_rapl: Found RAPL domain package
[   17.910830] intel_rapl: Found RAPL domain core
[   17.910832] intel_rapl: Found RAPL domain uncore
[   17.910834] intel_rapl: Found RAPL domain dram
[   17.910838] intel_rapl: RAPL package 0 domain package locked by BIOS
[   17.925627] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.926897] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffba8b81a00000, irq=19
[   17.928039] usb 2-5: new full-speed USB device number 6 using xhci_hcd
[   17.939812] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   18.374218] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   18.392340] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   18.401083] IPv6: ADDRCONF(NETDEV_UP): enp1s0f0: link is not ready
[   18.468490] IPv6: ADDRCONF(NETDEV_UP): enp1s0f0: link is not ready
[   18.595758] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   20.524721] wlp2s0: authenticate with ac:c6:62:8b:1b:30
[   20.549762] wlp2s0: send auth to ac:c6:62:8b:1b:30 (try 1/3)
[   20.551605] wlp2s0: authenticated
[   20.552488] wlp2s0: associating with AP with corrupt probe response
[   20.556047] wlp2s0: associate with ac:c6:62:8b:1b:30 (try 1/3)
[   20.558640] wlp2s0: RX AssocResp from ac:c6:62:8b:1b:30 (capab=0x31 status=0 aid=2)
[   20.558800] wlp2s0: associated
[   20.558895] ath: EEPROM regdomain: 0x804c
[   20.558897] ath: EEPROM indicates we should expect a country code
[   20.558898] ath: doing EEPROM country->regdmn map search
[   20.558899] ath: country maps to regdmn code: 0x3b
[   20.558900] ath: Country alpha2 being used: BR
[   20.558901] ath: Regpair used: 0x3b
[   20.558903] ath: regdomain 0x804c dynamically updated by country IE
[   20.676804] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   21.057801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.057804] Bluetooth: BNEP filters: protocol multicast
[   21.057810] Bluetooth: BNEP socket layer initialized
[   23.136038] usb 2-5: device descriptor read/64, error -110
[   28.533279] usb 2-5: New USB device found, idVendor=04ca, idProduct=300b, bcdDevice= 0.02
[   28.533283] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   28.727883] NET: Registered protocol family 38
[   30.219267] input: Designer Keyboard as /devices/virtual/misc/uhid/0005:0000:0000.0005/input/input21
[   30.219554] hid-generic 0005:0000:0000.0005: input,hidraw4: BLUETOOTH HID v0.00 Keyboard [Designer Keyboard] on 5C:C9:D3:F7:E6:13
[   35.696062] Bluetooth: RFCOMM TTY layer initialized
[   35.696070] Bluetooth: RFCOMM socket layer initialized
[   35.696077] Bluetooth: RFCOMM ver 1.11
[   36.312990] input: Designer Mouse as /devices/virtual/misc/uhid/0005:045E:0805.0006/input/input22
[   36.313225] hid-generic 0005:045E:0805.0006: input,hidraw5: BLUETOOTH HID v1.10 Mouse [Designer Mouse] on 5C:C9:D3:F7:E6:13
```

uname -a
```
Linux msmaldi-e1 4.17.1 #1 SMP Thu Jun 14 08:40:06 -03 2018 x86_64 x86_64 x86_64 GNU/Linux
```
I build a kernel, but problem continue.

lspci
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe (rev 01)
01:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 01)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
```

modinfo -p ath9k
```
debug:Debugging mask (uint)nohwcrypt:Disable hardware encryption (int)
blink:Enable LED blink on activity (int)
led_active_high:Invert LED polarity (int)
btcoex_enable:Enable wifi-BT coexistence (int)
bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
ps_enable:Enable WLAN PowerSave (int)
use_chanctx:Enable channel context for concurrency (int)
use_msi:Use MSI instead of INTx if possible (int)
```

I have same problem on deepin, elementary, ubuntu and debian, i have not tested in non-debian based linux, In windows 10 i have no problem.

i googled to many solutions for solve, but nothing resolve, i try:
```
echo "options ath9k btcoex_enable=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

```
modprobe ath9k btcoex_enable 1
```

```


########## wireless info START ##########


Report from: 14 Jun 2018 23:09 -03 -0300


Booted last: 14 Jun 2018 00:00 -03 -0300


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	elementary
Description:	elementary OS 0.4.1 Loki
Release:	0.4.1
Codename:	loki


##### kernel ############################


Linux 4.17.1 #1 SMP Thu Jun 14 08:40:06 -03 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Pantheon


##### lspci #############################


01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe [14e4:16b3] (rev 01)
	Subsystem: Acer Incorporated [ALI] NetXtreme BCM57786 Gigabit Ethernet PCIe [1025:0775]
	Kernel driver in use: tg3


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b3f6 Chicony Electronics Co., Ltd HD WebCam (Acer)
Bus 002 Device 006: ID 04ca:300b Lite-On Technology Corp. Atheros AR3012 Bluetooth
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 045e:070f Microsoft Corp. LifeChat LX-3000 Headset
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 151552  0
ath9k_common           24576  1 ath9k
ath9k_hw              479232  2 ath9k_common,ath9k
ath                    28672  3 ath9k_common,ath9k,ath9k_hw
mac80211              794624  1 ath9k
ath3k                  20480  0
bluetooth             548864  34 btrtl,btintel,btbcm,bnep,ath3k,btusb,rfcomm
cfg80211              663552  4 ath9k_common,ath9k,ath,mac80211
wmi_bmof               16384  0
wmi                    28672  1 wmi_bmof


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0f0  Link encap:Ethernet  HWaddr <MAC 'enp1s0f0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353169 (353.1 KB)  TX bytes:353169 (353.1 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.15.4  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: 2804:431:b705:187c:c9ef:aad4:a878:7e85/64 Scope:Global
          inet6 addr: 2804:431:b705:187c:85b5:1c8f:3332:dc8d/64 Scope:Global
          inet6 addr: fe80::b40a:cc96:fc91:272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91402375 (91.4 MB)  TX bytes:9814121 (9.8 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0f0  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"VIVO-1B30"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'VIVO-1B30' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:642   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.15.1    0.0.0.0         UG    600    0        0 wlp2s0
192.168.15.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       830     1  0 22:22 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.17.1
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     VIVO-1B30
GENERAL.CON-UUID:                       946a0990-e121-4715-80bd-ebe1633901a7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   946a0990-e121-4715-80bd-ebe1633901a7 | VIVO-1B30
IP4.ADDRESS[1]:                         192.168.15.4/24
IP4.GATEWAY:                            192.168.15.1
IP4.DNS[1]:                             192.168.15.1
IP4.WINS[1]:                            192.168.15.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.15.1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1529068930
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.15.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.15.4
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[20]:                       dhcp_lease_time = 43200
DHCP4.OPTION[21]:                       broadcast_address = 192.168.15.255
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.15.1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ntp_servers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       netbios_name_servers = 192.168.15.1
DHCP4.OPTION[28]:                       network_number = 192.168.15.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2804:431:b705:187c:c9ef:aad4:a878:7e85/64
IP6.ADDRESS[2]:                         2804:431:b705:187c:85b5:1c8f:3332:dc8d/64
IP6.ADDRESS[3]:                         fe80::b40a:cc96:fc91:272/64
IP6.GATEWAY:                            fe80::aec6:62ff:fe8b:1b30
IP6.ROUTE[1]:                           dst = 2804:431:b705:187c::/64, nh = fe80::aec6:62ff:fe8b:1b30, mt = 600
IP6.DNS[1]:                             fe80::aec6:62ff:fe8b:1b30
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::aec6:62ff:fe8b:1b30
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC 'VIVO-1B30' [AC1]>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_info_refresh_time = 43200
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:e8:64:8e:6f:b1:12:10:65:4c:81:f8:c5:92:c5:e2:28


GENERAL.DEVICE:                         enp1s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM57786 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp1s0f0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0f0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
VIVO-1B30  <MAC 'VIVO-1B30' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  yes     * 
MARINA     <MAC 'MARINA' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Willy2]] (600 root)
[connection] id=Willy2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Willy2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ALUNOS0]] (600 root)
[connection] id=ALUNOS0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ALUNOS0
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VIVO-1B30]] (600 root)
[connection] id=VIVO-1B30 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=VIVO-1B30
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Msmaldi]] (600 root)
[connection] id=Msmaldi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Msmaldi
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


country BR: DFS-FCC
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp1s0f0  no frequency information.


wlp2s0    13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0f0  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'VIVO-1B30' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"VIVO-1B30"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032b814d217
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MARINA' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"MARINA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bbd55b478
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.17.1/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5490BD93AF14078C36240EF
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.17.1 SMP mod_unload 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)


[ath9k_common]
filename:       /lib/modules/4.17.1/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     30B3A2A061A1A6FD62669EA
depends:        cfg80211,ath9k_hw,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.17.1 SMP mod_unload 


[ath9k_hw]
filename:       /lib/modules/4.17.1/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EE5706A10C7D8044088FCD8
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.17.1 SMP mod_unload 


[ath]
filename:       /lib/modules/4.17.1/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A26712513B0819E1D052245
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.17.1 SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.17.1/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8CFBFC715E5F80FE7675641
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.17.1 SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ath3k]
filename:       /lib/modules/4.17.1/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     602F81753874074553CEB2D
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       4.17.1 SMP mod_unload 


[cfg80211]
filename:       /lib/modules/4.17.1/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6B0DCB543FEDFD53405544D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.17.1 SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 1
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0
use_msi: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/ath9k-bt.conf]
options ath9k btcoex_enable=1


[/etc/modprobe.d/ath9k.conf]
options ath9k btcoex_enable=1


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist acer-wmi


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


rfkill unblock all


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   17.884402] ath: phy0: WB335 2-ANT card detected
[   17.884405] ath: phy0: Set BT/WLAN RX diversity capability
[   17.891774] ath: phy0: Enable LNA combining
[   17.895691] ath: phy0: ASPM enabled: 0x42
[   17.895694] ath: EEPROM regdomain: 0x65
[   17.895695] ath: EEPROM indicates we should expect a direct regpair map
[   17.895698] ath: Country alpha2 being used: 00
[   17.895699] ath: Regpair used: 0x65
[   17.939812] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   18.374218] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   18.401083] IPv6: ADDRCONF(NETDEV_UP): enp1s0f0: link is not ready (repeated 2 times)
[   18.595758] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   20.524721] wlp2s0: authenticate with <MAC 'VIVO-1B30' [AC1]>
[   20.549762] wlp2s0: send auth to <MAC 'VIVO-1B30' [AC1]> (try 1/3)
[   20.551605] wlp2s0: authenticated
[   20.552488] wlp2s0: associating with AP with corrupt probe response
[   20.556047] wlp2s0: associate with <MAC 'VIVO-1B30' [AC1]> (try 1/3)
[   20.558640] wlp2s0: RX AssocResp from <MAC 'VIVO-1B30' [AC1]> (capab=0x31 status=0 aid=2)
[   20.558800] wlp2s0: associated
[   20.558895] ath: EEPROM regdomain: 0x804c
[   20.558897] ath: EEPROM indicates we should expect a country code
[   20.558898] ath: doing EEPROM country->regdmn map search
[   20.558899] ath: country maps to regdmn code: 0x3b
[   20.558900] ath: Country alpha2 being used: BR
[   20.558901] ath: Regpair used: 0x3b
[   20.558903] ath: regdomain 0x804c dynamically updated by country IE
[   20.676804] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


########## wireless info END ############

```



can you help me?

---

### Post by jeremy31 on 2018-06-15
Moved to Ubuntu/Debian based

---

