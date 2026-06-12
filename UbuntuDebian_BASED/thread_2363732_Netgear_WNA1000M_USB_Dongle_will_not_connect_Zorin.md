---
title: "Netgear WNA1000M USB Dongle will not connect Zorin 12.1 Ultimate"
date: 2017-06-13
forum: Ubuntu/Debian BASED
---

### Post by namanati on 2017-06-13
First let me start off, I am a complete noob to linux.  

I have Zorin 12.1 Ultimate.  Fresh install.  WNA1000M USB Dongle (Netgear) is my network connection (which works in Windows 10 with no problems).  I have no ethernet to connect to, so I have to download everything via Windows, and then reboot into Zorin, as there is no way of connecting right now.

As for the connection itself, the light comes on the dongle, Zorin sees it and when I try to connect to it, it sees my network (WPA encryption), when I try to connect to it, it attempts to, and then just stops trying, and gives no error messages, or sometimes it completely locks up as well.

Any help would greatly be appreciated, and as I am a complete noob, please please explain it to me like I'm a 3 year old.

Thank you ahead of time,

---

### Post by QIII on 2017-06-13
Moved to ***Ubuntu/Debian BASED***

---

### Post by ajgreeny on 2017-06-13
Go to Wireless-info in my signature and download and run the script, then post back here the output you get.

This assumes the script will run in Zorin, which I think it should.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by namanati on 2017-06-13
> **ajgreeny said:**
> Go to Wireless-info in my signature and download and run the script, then post back here the output you get.

This assumes the script will run in Zorin, which I think it should.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Here is the requested information:

```

########## wireless info START ##########

Report from: 13 Jun 2017 16:13 EDT -0400

Booted last: 13 Jun 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Zorin
Description:    Zorin OS 12.1
Release:    12
Codename:    xenial

##### kernel ############################

Linux 4.8.0-39-generic #42~16.04.1-Ubuntu SMP Mon Feb 20 15:06:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company MCP61 Ethernet [103c:2a72]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 006: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 002: ID 0101:0007  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu              122880  0
rtl8192cu              65536  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              761856  4 rtl_usb,rtlwifi,rtl8192cu,rtl8xxxu
cfg80211              581632  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s7    Link encap:Ethernet  HWaddr <MAC 'enp0s7' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:262064 (262.0 KB)  TX bytes:262064 (262.0 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp0s7    no wireless extensions.

lo        no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1009     1  0 16:03 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.8.0-39-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.0/net/wlx<IF from MAC [IF2]>
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   284de6c2-c386-408d-9a7a-3e6734c125af | DG860AF2

GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
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

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DG860AF2        <MAC 'DG860AF2' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
MalcolmBaker    <MAC 'MalcolmBaker' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
CHARLIE & GALE  <MAC 'CHARLIE <MAC 'CHARLIE <MAC address> GALE' [AN3]> GALE' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        
ATT3M8H6q7      <MAC 'ATT3M8H6q7' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/DG860AF2]] (600 root)
[connection] id=DG860AF2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=DG860AF2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG860AF2.AYZK1Y]] (600 root)
[connection] id=DG860AF2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=DG860AF2
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

enp0s7    no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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

##### iwlist scan #######################

enp0s7    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'DG860AF2' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"DG860AF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004550aab7a
                    Extra: Last beacon: 736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'CHARLIE <MAC 'CHARLIE <MAC address> GALE' [AN3]> GALE' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"CHARLIE & GALE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a6841192
                    Extra: Last beacon: 472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MalcolmBaker' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"MalcolmBaker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002132a724a
                    Extra: Last beacon: 460ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     59F02B6CF781E1985E0D1CE
depends:        mac80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[rtl8192cu]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     7FD327046ED7ECB8EE1DA58
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2726AF7744B82E7E490A960
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FF42529D1B19DDAF0323975
depends:        rtlwifi
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B936ED0E7D6B2CC6861A1AE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug: 0
swenc: N

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

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[   14.485018] rtl8192cu: Chip version 0x10
[   14.575749] rtl8192cu: Board Type 0
[   14.575987] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   14.576062] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   14.645521] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.516666] rtl8192cu 1-3.3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   24.924448] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   24.926486] rtl8192cu: MAC auto ON okay!
[   24.959619] rtl8192cu: Tx queue select: 0x05
[   25.457316] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   25.466132] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   25.466706] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[   25.466921] forcedeth 0000:00:07.0 enp0s7: no link during initialization
[   25.467223] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   25.910402] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready

########## wireless info END ############



```

Hopefully I did that correctly.  Thank you ahead of time for your help.

---

### Post by namanati on 2017-06-14
Did I not post it correctly, or did I mess something up, or does it just take a little time (which is alright), I just don't know how this stuff normally works for non-windows stuff, which I am trying to desperately get away from now.

Thanks ahead of time, and hopefully we can get this taken care of, so I can dive into learning the rest of the platform OS.

---

### Post by gordintoronto on 2017-06-15
Google often provides an answer, the trick is to know what to search for. Your wireless adapter is an RTL8188CUS, which took me to this site:
[https://crunchbang.org/forums/viewtopic.php?id=40015](https://crunchbang.org/forums/viewtopic.php?id=40015)

I hope you find it useful.

---

### Post by namanati on 2017-06-16
> **gordintoronto said:**
> Google often provides an answer, the trick is to know what to search for. Your wireless adapter is an RTL8188CUS, which took me to this site:
[https://crunchbang.org/forums/viewtopic.php?id=40015](https://crunchbang.org/forums/viewtopic.php?id=40015)

I hope you find it useful.

First, on the Google often provides an answer:  When looking for my problem (which I have no idea about the Realtek 81** logic listed in that post, as my Dongle is a Netgear), there are  literally hundreds of pages available and unless one (which is not me) knows exactly what can be trusted, and what is just sales sites, or junk sites, it is impossible to go through all that to figure it out quickly.  That is why I came to the Ubuntu question to ask about an Ubuntu related problem.  I am open to learning how to do this, but please remember, my OP states, explain it like I'm a 3 year old (cause where anything linux and even drivers are concerned I am).  What is the logic that brought you to search for RTL drivers, how do you come across which number, what did you end up using as your search parameter, how did you decided what was to be trusted, etc, etc.  

Secondly, those instructions require you to be hooked to internet via ethernet or whatever way while your in the distro, which as I stated originally I can't do.  I need to find a way to do these things by logging into my Windows, downloading whatever is needed, then go back to the Zorin and utilizing downloaded files that way.  Those are the type of instructions I need, and I have no clue how to do these things in Linux/Ubuntu/Zorin/etc.  I did follow some help tutorials from Chili back in 2011, and again in 2013 that are on the web, however, now the computer just locks up every time it tries to connect.  The two sets of instructions I followed were located at: [https://ubuntuforums.org/showthread.php?t=1806839](https://ubuntuforums.org/showthread.php?t=1806839) and [https://ubuntuforums.org/showthread.php?t=2184113.]("https://ubuntuforums.org/showthread.php?t=2184113")

Again, thank you ahead of time.

---

### Post by namanati on 2017-06-16
Not sure if this helps, but installed my earlier version of Zorin 11 Ultimate, and the same adapter works with it.  Not sure why it would stop working with a newer version, but apparently it does.  Please help.

---

