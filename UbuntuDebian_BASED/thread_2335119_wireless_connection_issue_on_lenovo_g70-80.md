---
title: "wireless connection issue on lenovo g70-80"
date: 2016-08-25
forum: Ubuntu/Debian BASED
---

### Post by ripplingj on 2016-08-25
wireless connection issue on lenovo g70-80

i was able to install the wireless to see the networks by following other forums now the wireless will not connect 

i ran the script and got this 
```


########## wireless info START ##########

Report from: 25 Aug 2016 12:55 EDT -0400

Booted last: 25 Aug 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Zorin
Description:    Zorin 11
Release:    11
Codename:    wily

##### kernel ############################

Linux 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Zorin Desktop

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3819]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 005: ID 13d3:5727 IMC Networks 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           274432  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              643072  1 ath10k_core
cfg80211              540672  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:296907553 (296.9 MB)  TX bytes:8115961 (8.1 MB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       610     1  0 12:36 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c6b6a685-dadf-4654-b1ce-04a0be1989a5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c6b6a685-dadf-4654-b1ce-04a0be1989a5 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.37/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1472229732
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.37
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF1]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Wildcat Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.2.0-23-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/DaNet]] (600 root)
[connection] id=DaNet | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=DaNet
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/DIRECT-roku-809-9FA8D9]] (600 root)
[connection] id=DIRECT-roku-809-9FA8D9 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=DIRECT-roku-809-9FA8D9
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp3s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-23-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
srcversion:     546811EFF3C7A8D4FB20A07
depends:        ath10k_core,compat
vermagic:       4.2.0-23-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-23-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     B8B903F0D843C312F7FCB10
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-23-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.2.0-23-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       4.2.0-23-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-23-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
srcversion:     94D2A0276F31273C6A42278
depends:        cfg80211,compat
vermagic:       4.2.0-23-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-23-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6BE4ED42578C9DFBE16CE50
depends:        compat
vermagic:       4.2.0-23-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: Y
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  919.046136] ath10k_pci 0000:03:00.0: failed to setup ps on vdev 0: -108
[  919.046146] ath10k_pci 0000:03:00.0: device successfully recovered
[  920.552907] ath10k_pci 0000:03:00.0: firmware crashed! (uuid b6fbe133-f04e-49d9-bf6c-c42832433101)
[  920.552922] ath10k_pci 0000:03:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 features \xffffffd8=\xffffffc0^\xffffff88\xffffffff\xffffffff\xffffff98=\xffffffc0^\xffffff88\xffffffff\xffffffffhL\xffffffa1Y\xffffff8dW\xffffffb7T\xffffffc5Q\xffffffc0\xffffffff\xffffffff\xffffffff\xffffffff2
[  920.552926] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[  920.554936] ath10k_pci 0000:03:00.0: firmware register dump:
[  920.554943] ath10k_pci 0000:03:00.0: [00]: 0x05010000 0x000015B3 0x00939797 0x00955B31
[  920.554946] ath10k_pci 0000:03:00.0: [04]: 0x00939797 0x00060330 0x00000000 0x0041A92C
[  920.554950] ath10k_pci 0000:03:00.0: [08]: 0x00413A18 0x0000FFFF 0x00000000 0x00000000
[  920.554954] ath10k_pci 0000:03:00.0: [12]: 0x00000009 0xFFFFFFFF 0x0096C09C 0x0096C0A7
[  920.554957] ath10k_pci 0000:03:00.0: [16]: 0x0096BDBC 0x000B49C7 0x00000000 0x00000000
[  920.554960] ath10k_pci 0000:03:00.0: [20]: 0x40939797 0x0041A7D0 0x00407124 0x00000000
[  920.554964] ath10k_pci 0000:03:00.0: [24]: 0x8093D6C4 0x0041A830 0x00400000 0xC0939797
[  920.554967] ath10k_pci 0000:03:00.0: [28]: 0x8094777F 0x0041A850 0x0046D5D8 0x00000001
[  920.554970] ath10k_pci 0000:03:00.0: [32]: 0x800AA334 0x0041A880 0x0046D5D8 0x00000001
[  920.554974] ath10k_pci 0000:03:00.0: [36]: 0x800AA49E 0x0041A8A0 0x00424944 0x00000001
[  920.554977] ath10k_pci 0000:03:00.0: [40]: 0x80994E3A 0x0041A8C0 0x00424944 0x0041A908
[  920.554980] ath10k_pci 0000:03:00.0: [44]: 0x80996E7A 0x0041A8F0 0x0046F888 0x00412984
[  920.554983] ath10k_pci 0000:03:00.0: [48]: 0x800B49E9 0x0041A930 0x00422484 0x00005008
[  920.554986] ath10k_pci 0000:03:00.0: [52]: 0x809A6C5C 0x0041A9C0 0x0042942C 0x0042CB4C
[  920.554989] ath10k_pci 0000:03:00.0: [56]: 0x809A62B0 0x0041AA00 0x0041AA24 0x00427230
[  920.555031] ath10k_pci 0000:03:00.0: failed to set vdev 0 up: -108
[  920.555037] ath10k_pci 0000:03:00.0: failed to set 2g txpower 0: -108
[  927.539509] wlp3s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  927.539619] ath10k_warn: 6 callbacks suppressed
[  927.539629] ath10k_pci 0000:03:00.0: failed to delete peer <MAC address> for vdev 0: -108
[  927.539667] ath10k_pci 0000:03:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[  927.539672] ath10k_pci 0000:03:00.0: failed to set protection mode 0 on vdev 0: -108
[  927.539675] ath10k_pci 0000:03:00.0: failed to set erp slot for vdev 0: -108
[  927.539679] ath10k_pci 0000:03:00.0: failed to set preamble for vdev 0: -108
[  927.539683] ath10k_pci 0000:03:00.0: faield to down vdev 0: -108
[  927.539688] ath10k_pci 0000:03:00.0: failed to submit vdev param txbf 0x0: -108
[  927.539691] ath10k_pci 0000:03:00.0: failed to recalc txbf for vdev 0: -108
[  927.539696] ath10k_pci 0000:03:00.0: failed to set vdev wmm params on vdev 0: -108 (repeated 2 times)
[  932.649190] ath10k_warn: 9 callbacks suppressed
[  932.649196] ath10k_pci 0000:03:00.0: failed to start hw scan: -108 (repeated 10 times)
[  944.782169] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  944.788125] ath10k_pci 0000:03:00.0: failed to start hw scan: -108
[  946.752941] ath10k_pci 0000:03:00.0: failed to delete WMI vdev 0: -108
[  946.752947] ath10k_pci 0000:03:00.0: removing stale peer <MAC address> from vdev_id 0
[  948.483494] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  948.483978] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108 (repeated 2 times)
[  948.490279] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  951.412571] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  951.497302] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  952.623849] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  952.624271] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  954.713676] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  954.714282] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  962.057855] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  962.058493] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  963.939112] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  963.939786] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  964.347508] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  964.348080] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  964.523879] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  964.524522] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  972.580012] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  972.580603] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  974.991477] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  974.992058] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  975.198286] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  975.198783] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  980.408080] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  980.409894] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  986.273556] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  986.274165] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  988.083738] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[  988.084334] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 1041.752923] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[ 1041.753768] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 1045.621337] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[ 1045.621982] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 1046.902141] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[ 1046.902766] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 1049.008331] ath10k_pci 0000:03:00.0: failed to create WMI vdev 0: -108
[ 1049.008963] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2016-08-25
Moved tu Ubuntu/Debian based
Is there a Zorin version based on Ubuntu 16.04?  That would eliminate some issues

---

### Post by ripplingj on 2016-08-25
Its zorin 11 based on Ubuntu 15.10

---

### Post by jeremy31 on 2016-08-25
I would uninstall the current backports
```
cd backports-20150731
sudo make uninstall
```
Download newer ones from [https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz)
I don't know why it looks like it was from March 24, 2016 but the last update was July 13.  Extract and install these
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz
tar -zxvf backports-20160324.tar.gz
cd backports-20160324
make defconfig-ath10k
make 
sudo make install
```

Then get the latest firmware
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.3_all.deb
sudo dpkg -i linux-firmware_1.157.3_all.deb
```

reboot

---

### Post by ripplingj on 2016-08-26
i tried the make defconfig ath10k

make[1]: *** No rule to make target 'defconfig'.  Stop.
Makefile:40: recipe for target 'defconfig' failed
make: *** [defconfig] Error 2

i got a failure now there are no wireless in networks

---

### Post by jeremy31 on 2016-08-26
I missed a - again ```
make defconfig-ath10k
```

---

### Post by ripplingj on 2016-08-26
this works thank you very much !!!!

---

