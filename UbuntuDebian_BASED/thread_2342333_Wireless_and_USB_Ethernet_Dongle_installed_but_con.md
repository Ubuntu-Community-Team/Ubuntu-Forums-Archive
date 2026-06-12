---
title: "Wireless and USB Ethernet Dongle installed but connection hangs"
date: 2016-11-05
forum: Ubuntu/Debian BASED
---

### Post by adameast9000 on 2016-11-05
Hi I have an Acer Chromebook C720 running GalliumOS (a distro that includes lots of chromebook drivers). I recently let the battery run out by not using it for a few weeks and now the internet won't connect over wifi (can see the networks and tries to connect but gives up after a while of trying) or ethernet (bought a PnP dongle for the occasion, same problem of trying to connect for a while then giving up). I've run the standard network info script from the sticky on this forum and it's below. Anyone have an idea on this? Thanks.

```



########## wireless info START ##########


Report from: 22 Dec 2148 05:43 EST -0500


Booted last: 22 Dec 2148 00:00 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    GalliumOS 2.0
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.6-galliumos #2 SMP PREEMPT Fri Apr 29 13:30:57 MDT 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, tpm_tis.interrupts=0, i915.enable_ips=0, vt.handoff=7


##### desktop ###########################


/usr/bin/startxfce4


##### lspci #############################


01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter [105b:e058]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 002: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:8152 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 002: ID 04f2:b490 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              733184  1 ath9k
ath3k                  20480  0
cfg80211              552960  4 ath,ath9k_common,ath9k,mac80211
bluetooth             516096  40 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enx<IF from MAC [IF1]>  no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2222     1  0 05:10 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9462 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.6-galliumos
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{22}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e8a90df-728b-4fba-a5ac-174525f667b8 | SlowInternetDon'tSteal_2G


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         CMI
GENERAL.PRODUCT:                        USB 10/100 LAN
GENERAL.DRIVER:                         r8152
GENERAL.DRIVER-VERSION:                 v1.08.2
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/net/enx<IF from MAC [IF1]>
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


SSID                       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
HamHouse2G                 <MAC 'HamHouse2G' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
SlowInternetDon'tSteal_2G  <MAC 'SlowInternetDon'tSteal_2G' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
HamHouse5G                 <MAC 'HamHouse5G' [AC3]>  Infra  153   5765 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2      no        
--                         <MAC '' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2      no        
--                         <MAC '' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2      no        
--                         <MAC '' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WEP       no        
SlowInternetDon'tSteal_5G  <MAC 'SlowInternetDon'tSteal_5G' [AC2]>  Infra  36    5180 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2      no        
Beach-Guest                <MAC 'Beach-Guest' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --        no        
--                         <MAC '             ' [AC5]>  Infra  36    5180 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2      no        
OceanPebbles               <MAC 'OceanPebbles' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2      no        
--                         <MAC '' [AC6]>  Infra  161   5805 MHz  0 Mbit/s   29      &#9602;___  WEP       no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SlowInternetDon'tSteal_2G]] (600 root)
[connection] id=SlowInternetDon'tSteal_2G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=SlowInternetDon'tSteal_2G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Nassau (based on set time zone)


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


enx<IF from MAC [IF1]>  no frequency information.


lo        no frequency information.


wlp1s0    32 channels in total; available frequencies :
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


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.765 GHz
      1   APs on   Frequency:5.805 GHz


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'HamHouse2G' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"HamHouse2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000024d3b7e7d
                    Extra: Last beacon: 49ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SlowInternetDon'tSteal_5G' [AC2]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"SlowInternetDon'tSteal_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000842696cc50
                    Extra: Last beacon: 49ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HamHouse5G' [AC3]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"HamHouse5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024d659503
                    Extra: Last beacon: 49ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SlowInternetDon'tSteal_2G' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"SlowInternetDon'tSteal_2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000842719c091
                    Extra: Last beacon: 49ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '             ' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000842528127c
                    Extra: Last beacon: 26619ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=00000012608da02b
                    Extra: Last beacon: 223ms ago
          Cell 07 - Address: <MAC 'OceanPebbles' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"OceanPebbles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001305a10196
                    Extra: Last beacon: 27560ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Beach-Guest' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"Beach-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001305a10b3c
                    Extra: Last beacon: 27558ms ago
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c832467
                    Extra: Last beacon: 3207ms ago
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c8325b0
                    Extra: Last beacon: 3207ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c8326a4
                    Extra: Last beacon: 3207ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.4.6-galliumos/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.6-galliumos/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.6-galliumos/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     26A41940D620A49C2442ACF
depends:        ath
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.6-galliumos/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.6-galliumos/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ath3k]
filename:       /lib/modules/4.4.6-galliumos/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     9387708AAFFA4D924D90966
depends:        bluetooth
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.4.6-galliumos/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.6-galliumos SMP preempt mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 1
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k btcoex_enable=1 nohwcrypt=1


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


[/etc/modprobe.d/blacklist-lp.conf]
blacklist lp
blacklist ppdev
blacklist parport_pc


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


[/etc/modprobe.d/snd-hda-intel.conf]
options snd-hda-intel model=,alc283-dac-wcaps


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############

```

---

### Post by jeremy31 on 2016-11-05
*Thread moved to **Ubuntu/Debian BASED**.*

Not much tx-power in the results, see if 
```
sudo iwconfig wlp1s0 txpower 17
```

Set the country code with ```

sudo iw reg set BS
sudo sed -i 's/^REG.*=$/&BS/' /etc/default/crda

```
Reboot and see if it is enough

---

### Post by adameast9000 on 2016-11-05
Unfortunately not. Same issue

---

### Post by jeremy31 on 2016-11-05
Did the tx-power change in the results for ```
iwconfig
```
It was at a mere 3 dBm

---

### Post by adameast9000 on 2016-11-05
after restart it got reset to 3 dBm. I just ran it again and immediately checked it and now it's at 15 dB, but still same problem. This would also not explain why ethernet is having same problem...

---

### Post by adameast9000 on 2016-11-05
Tried this again to test. The command does change the txpower, but restarting resets it to 3. Could be a chromebook thing

---

